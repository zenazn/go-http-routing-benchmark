go-http-routing-benchmark
=========================

This benchmark suite aims to compare the performance of available HTTP request routers for Go by implementing the routing of some real world APIs.
Some of the APIs are slightly adapted, since they can not be implemented 1:1 in some of the routers.


Included Routers:

 * [Gocraft Web](https://github.com/gocraft/web)
 * [Gorilla Mux](http://www.gorillatoolkit.org/pkg/mux)
 * [net/http.ServeMux](http://golang.org/pkg/net/http/#ServeMux)
 * [HttpRouter](https://github.com/julienschmidt/httprouter)
 * [Martini](https://github.com/codegangsta/martini)
 * [Pat](https://github.com/bmizerany/pat)
 * [TigerTonic](https://github.com/rcrowley/go-tigertonic)
 * [Traffic](https://github.com/pilu/traffic)
 * [Goji](https://github.com/zenazn/goji)

## Results

Benchmark System:
 * Mid-2012 15" Retina MacBook Pro
 * 2.6 GHz Intel Core i7 (i7-3720QM)
 * 16 GB 1600 MHz DDR3
 * go1.2 darwin/amd64
 * OS X 10.9.2
 * Run with `go test -bench=. 2>/dev/null`

```
#GithubAPI Routes: 203
#GPlusAPI Routes: 13
#ParseAPI Routes: 26
#Static Routes: 157

BenchmarkGocraftWeb_Param            1000000       1616 ns/op         672 B/op        9 allocs/op
BenchmarkGorillaMux_Param             500000       4723 ns/op         785 B/op        7 allocs/op
BenchmarkHttpRouter_Param            5000000        543 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_Param                500000       5956 ns/op        1184 B/op       13 allocs/op
BenchmarkPat_Param                   1000000       2565 ns/op        1060 B/op       17 allocs/op
BenchmarkTigerTonic_Param            1000000       2358 ns/op         829 B/op       16 allocs/op
BenchmarkTraffic_Param                500000       5845 ns/op        2022 B/op       23 allocs/op
BenchmarkGoji_Param                  2000000        863 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_Param20           200000       7805 ns/op        3863 B/op       17 allocs/op
BenchmarkGorillaMux_Param20           100000      17179 ns/op        3310 B/op       10 allocs/op
BenchmarkHttpRouter_Param20           500000       4898 ns/op        2218 B/op        4 allocs/op
BenchmarkMartini_Param20               50000      56607 ns/op        3711 B/op       16 allocs/op
BenchmarkPat_Param20                  100000      24175 ns/op        5728 B/op      154 allocs/op
BenchmarkTigerTonic_Param20            50000      39914 ns/op       11062 B/op      176 allocs/op
BenchmarkTraffic_Param20               50000      29496 ns/op        8227 B/op       67 allocs/op
BenchmarkGoji_Param20                 500000       3499 ns/op        1260 B/op        2 allocs/op

BenchmarkGocraftWeb_ParamWrite       1000000       1762 ns/op         681 B/op       10 allocs/op
BenchmarkGorillaMux_ParamWrite        500000       5078 ns/op         785 B/op        7 allocs/op
BenchmarkHttpRouter_ParamWrite       5000000        592 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_ParamWrite           200000       7183 ns/op        1284 B/op       16 allocs/op
BenchmarkPat_ParamWrite              1000000       3219 ns/op        1127 B/op       19 allocs/op
BenchmarkTigerTonic_ParamWrite        500000       4682 ns/op        1287 B/op       22 allocs/op
BenchmarkTraffic_ParamWrite           500000       7021 ns/op        2455 B/op       27 allocs/op
BenchmarkGoji_ParamWrite             2000000        835 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_GithubStatic     1000000       1078 ns/op         313 B/op        6 allocs/op
BenchmarkGorillaMux_GithubStatic       50000      37946 ns/op         459 B/op        6 allocs/op
BenchmarkHttpRouter_GithubStatic    50000000       58.8 ns/op           0 B/op        0 allocs/op
BenchmarkMartini_GithubStatic         100000      19643 ns/op         858 B/op       12 allocs/op
BenchmarkPat_GithubStatic             200000      12475 ns/op        3787 B/op       76 allocs/op
BenchmarkTigerTonic_GithubStatic     5000000        334 ns/op          49 B/op        1 allocs/op
BenchmarkTraffic_GithubStatic          50000      65161 ns/op       23355 B/op      172 allocs/op
BenchmarkGoji_GithubStatic           5000000        407 ns/op           0 B/op        0 allocs/op

BenchmarkGocraftWeb_GithubParam      1000000       2000 ns/op         735 B/op       10 allocs/op
BenchmarkGorillaMux_GithubParam       100000      25228 ns/op         818 B/op        7 allocs/op
BenchmarkHttpRouter_GithubParam      5000000        741 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_GithubParam          100000      22704 ns/op        1218 B/op       13 allocs/op
BenchmarkPat_GithubParam              200000       8497 ns/op        2623 B/op       56 allocs/op
BenchmarkTigerTonic_GithubParam       500000       4596 ns/op        1288 B/op       25 allocs/op
BenchmarkTraffic_GithubParam          100000      28703 ns/op        7145 B/op       60 allocs/op
BenchmarkGoji_GithubParam            1000000       1450 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_GithubAll           5000     397279 ns/op      136203 B/op     1914 allocs/op
BenchmarkGorillaMux_GithubAll            100   15127892 ns/op      153228 B/op     1419 allocs/op
BenchmarkHttpRouter_GithubAll          10000     123679 ns/op       57334 B/op      347 allocs/op
BenchmarkMartini_GithubAll               200    9673593 ns/op      245095 B/op     2939 allocs/op
BenchmarkPat_GithubAll                   500    4416859 ns/op     1587626 B/op    32569 allocs/op
BenchmarkTigerTonic_GithubAll           2000     876237 ns/op      218073 B/op     5581 allocs/op
BenchmarkTraffic_GithubAll               100   13024934 ns/op     3171102 B/op    24920 allocs/op
BenchmarkGoji_GithubAll                 5000     624272 ns/op       57285 B/op      347 allocs/op

BenchmarkGocraftWeb_GPlusStatic      2000000        925 ns/op         297 B/op        6 allocs/op
BenchmarkGorillaMux_GPlusStatic       500000       3541 ns/op         459 B/op        6 allocs/op
BenchmarkHttpRouter_GPlusStatic     50000000       31.9 ns/op           0 B/op        0 allocs/op
BenchmarkMartini_GPlusStatic          500000       4593 ns/op         859 B/op       12 allocs/op
BenchmarkPat_GPlusStatic             5000000        346 ns/op          99 B/op        2 allocs/op
BenchmarkTigerTonic_GPlusStatic     10000000        190 ns/op          33 B/op        1 allocs/op
BenchmarkTraffic_GPlusStatic          500000       4601 ns/op        1508 B/op       19 allocs/op
BenchmarkGoji_GPlusStatic           10000000        279 ns/op           0 B/op        0 allocs/op

BenchmarkGocraftWeb_GPlusParam       1000000       1653 ns/op         672 B/op        9 allocs/op
BenchmarkGorillaMux_GPlusParam        200000       7892 ns/op         785 B/op        7 allocs/op
BenchmarkHttpRouter_GPlusParam       5000000        589 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_GPlusParam           200000       8400 ns/op        1185 B/op       13 allocs/op
BenchmarkPat_GPlusParam              1000000       2025 ns/op         752 B/op       14 allocs/op
BenchmarkTigerTonic_GPlusParam       1000000       2797 ns/op         907 B/op       16 allocs/op
BenchmarkTraffic_GPlusParam           500000       7482 ns/op        2037 B/op       23 allocs/op
BenchmarkGoji_GPlusParam             2000000        915 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_GPlus2Params     1000000       2045 ns/op         735 B/op       10 allocs/op
BenchmarkGorillaMux_GPlus2Params      100000      21768 ns/op         818 B/op        7 allocs/op
BenchmarkHttpRouter_GPlus2Params     5000000        675 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_GPlus2Params         100000      26937 ns/op        1317 B/op       17 allocs/op
BenchmarkPat_GPlus2Params             500000       6430 ns/op        2398 B/op       41 allocs/op
BenchmarkTigerTonic_GPlus2Params      500000       4785 ns/op        1390 B/op       25 allocs/op
BenchmarkTraffic_GPlus2Params         100000      23390 ns/op        3617 B/op       35 allocs/op
BenchmarkGoji_GPlus2Params           1000000       1357 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_GPlusAll          100000      22227 ns/op        8333 B/op      117 allocs/op
BenchmarkGorillaMux_GPlusAll           10000     138057 ns/op        9721 B/op       91 allocs/op
BenchmarkHttpRouter_GPlusAll          500000       7223 ns/op        3773 B/op       22 allocs/op
BenchmarkMartini_GPlusAll              10000     157286 ns/op       15515 B/op      194 allocs/op
BenchmarkPat_GPlusAll                  50000      51153 ns/op       17678 B/op      346 allocs/op
BenchmarkTigerTonic_GPlusAll           50000      46958 ns/op       13322 B/op      289 allocs/op
BenchmarkTraffic_GPlusAll              10000     161653 ns/op       42030 B/op      446 allocs/op
BenchmarkGoji_GPlusAll                200000      12689 ns/op        3773 B/op       22 allocs/op

BenchmarkGocraftWeb_ParseStatic      2000000        967 ns/op         313 B/op        6 allocs/op
BenchmarkGorillaMux_ParseStatic       500000       6962 ns/op         459 B/op        6 allocs/op
BenchmarkHttpRouter_ParseStatic     50000000       32.3 ns/op           0 B/op        0 allocs/op
BenchmarkMartini_ParseStatic          500000       5266 ns/op         859 B/op       12 allocs/op
BenchmarkPat_ParseStatic             2000000        826 ns/op         249 B/op        5 allocs/op
BenchmarkTigerTonic_ParseStatic     10000000        267 ns/op          49 B/op        1 allocs/op
BenchmarkTraffic_ParseStatic          500000       7368 ns/op        2388 B/op       25 allocs/op
BenchmarkGoji_ParseStatic            5000000        334 ns/op           0 B/op        0 allocs/op

BenchmarkGocraftWeb_ParseParam       1000000       1699 ns/op         688 B/op        9 allocs/op
BenchmarkGorillaMux_ParseParam        200000       7777 ns/op         785 B/op        7 allocs/op
BenchmarkHttpRouter_ParseParam       5000000        587 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_ParseParam           500000       7717 ns/op        1185 B/op       13 allocs/op
BenchmarkPat_ParseParam              1000000       2944 ns/op        1196 B/op       20 allocs/op
BenchmarkTigerTonic_ParseParam       1000000       2658 ns/op         888 B/op       16 allocs/op
BenchmarkTraffic_ParseParam           500000       7567 ns/op        2322 B/op       25 allocs/op
BenchmarkGoji_ParseParam             1000000       1069 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_Parse2Params     1000000       1943 ns/op         735 B/op       10 allocs/op
BenchmarkGorillaMux_Parse2Params      200000       7845 ns/op         818 B/op        7 allocs/op
BenchmarkHttpRouter_Parse2Params     5000000        634 ns/op         343 B/op        2 allocs/op
BenchmarkMartini_Parse2Params         200000       7469 ns/op        1218 B/op       13 allocs/op
BenchmarkPat_Parse2Params            1000000       2870 ns/op         907 B/op       21 allocs/op
BenchmarkTigerTonic_Parse2Params      500000       4465 ns/op        1293 B/op       25 allocs/op
BenchmarkTraffic_Parse2Params         500000       7312 ns/op        2128 B/op       25 allocs/op
BenchmarkGoji_Parse2Params           1000000       1031 ns/op         343 B/op        2 allocs/op

BenchmarkGocraftWeb_ParseAll           50000      39315 ns/op       14286 B/op      209 allocs/op
BenchmarkGorillaMux_ParseAll           10000     292755 ns/op       17249 B/op      175 allocs/op
BenchmarkHttpRouter_ParseAll          200000      10776 ns/op        5488 B/op       33 allocs/op
BenchmarkMartini_ParseAll              10000     196389 ns/op       27659 B/op      333 allocs/op
BenchmarkPat_ParseAll                  50000      56116 ns/op       18265 B/op      385 allocs/op
BenchmarkTigerTonic_ParseAll           50000      61981 ns/op       17721 B/op      372 allocs/op
BenchmarkTraffic_ParseAll              10000     235172 ns/op       70485 B/op      762 allocs/op
BenchmarkGoji_ParseAll                100000      20825 ns/op        5489 B/op       33 allocs/op

BenchmarkHttpServeMux_StaticAll         2000    1091974 ns/op         104 B/op        8 allocs/op
BenchmarkGocraftWeb_StaticAll          10000     175024 ns/op       49134 B/op      951 allocs/op
BenchmarkGorillaMux_StaticAll            500    4655748 ns/op       72270 B/op      965 allocs/op
BenchmarkHttpRouter_StaticAll         100000      16620 ns/op           0 B/op        0 allocs/op
BenchmarkMartini_StaticAll               500    3461405 ns/op      145534 B/op     2520 allocs/op
BenchmarkPat_StaticAll                  1000    1703014 ns/op      554060 B/op    11248 allocs/op
BenchmarkTigerTonic_StaticAll          50000      63549 ns/op        7775 B/op      158 allocs/op
BenchmarkTraffic_StaticAll               100   11243759 ns/op     3792778 B/op    27904 allocs/op
BenchmarkGoji_StaticAll                20000      80467 ns/op           0 B/op        0 allocs/op
```
