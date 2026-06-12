---
title: "Possible break in attempt"
date: 2009-07-06
forum: Security
---

### Post by triangleSLO on 2009-07-06
I am new to ssh and maybe a little too paranoid. Should i be worried by this log?
```
Jul  5 11:39:48 primorec sshd[5093]: Connection from 77.240.189.2 port 49746
Jul  5 11:39:48 primorec sshd[5093]: Did not receive identification string from 77.240.189.2
Jul  5 11:55:53 primorec sshd[6028]: Connection from 77.240.189.2 port 45031
Jul  5 11:55:54 primorec sshd[6028]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:54 primorec sshd[6028]: Invalid user test from 77.240.189.2
Jul  5 11:55:54 primorec sshd[6030]: Connection from 77.240.189.2 port 45141
Jul  5 11:55:55 primorec sshd[6030]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:55 primorec sshd[6030]: Invalid user test from 77.240.189.2
Jul  5 11:55:55 primorec sshd[6032]: Connection from 77.240.189.2 port 45273
Jul  5 11:55:56 primorec sshd[6032]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:56 primorec sshd[6032]: Invalid user test from 77.240.189.2
Jul  5 11:55:56 primorec sshd[6034]: Connection from 77.240.189.2 port 45403
Jul  5 11:55:57 primorec sshd[6034]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:57 primorec sshd[6034]: Invalid user test from 77.240.189.2
Jul  5 11:55:57 primorec sshd[6036]: Connection from 77.240.189.2 port 45520
Jul  5 11:55:57 primorec sshd[6036]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:57 primorec sshd[6036]: Invalid user test from 77.240.189.2
Jul  5 11:55:58 primorec sshd[6038]: Connection from 77.240.189.2 port 45634
Jul  5 11:55:58 primorec sshd[6038]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:58 primorec sshd[6038]: Invalid user test from 77.240.189.2
Jul  5 11:55:58 primorec sshd[6040]: Connection from 77.240.189.2 port 45765
Jul  5 11:55:59 primorec sshd[6040]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:59 primorec sshd[6040]: Invalid user test from 77.240.189.2
Jul  5 11:55:59 primorec sshd[6042]: Connection from 77.240.189.2 port 45879
Jul  5 11:56:00 primorec sshd[6042]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:00 primorec sshd[6042]: Invalid user test from 77.240.189.2
Jul  5 11:56:00 primorec sshd[6044]: Connection from 77.240.189.2 port 45980
Jul  5 11:56:01 primorec sshd[6044]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:01 primorec sshd[6044]: Invalid user test from 77.240.189.2
Jul  5 11:56:01 primorec sshd[6046]: Connection from 77.240.189.2 port 46101
Jul  5 11:56:01 primorec sshd[6046]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:01 primorec sshd[6046]: Invalid user test from 77.240.189.2
Jul  5 11:56:02 primorec sshd[6048]: Connection from 77.240.189.2 port 46224
Jul  5 11:56:02 primorec sshd[6048]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:02 primorec sshd[6048]: Invalid user test from 77.240.189.2
Jul  5 11:56:02 primorec sshd[6050]: Connection from 77.240.189.2 port 46317
Jul  5 11:56:03 primorec sshd[6050]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:03 primorec sshd[6050]: Invalid user test from 77.240.189.2
Jul  5 11:56:03 primorec sshd[6052]: Connection from 77.240.189.2 port 46433
Jul  5 11:56:04 primorec sshd[6052]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:04 primorec sshd[6052]: Invalid user test from 77.240.189.2
Jul  5 11:56:04 primorec sshd[6054]: Connection from 77.240.189.2 port 46535
Jul  5 11:56:05 primorec sshd[6054]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:05 primorec sshd[6054]: Invalid user test from 77.240.189.2
Jul  5 11:56:05 primorec sshd[6056]: Connection from 77.240.189.2 port 46674
Jul  5 11:56:06 primorec sshd[6056]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:06 primorec sshd[6056]: Invalid user test from 77.240.189.2
Jul  5 11:56:06 primorec sshd[6058]: Connection from 77.240.189.2 port 46772
Jul  5 11:56:06 primorec sshd[6058]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:06 primorec sshd[6058]: Invalid user test from 77.240.189.2
Jul  5 11:56:07 primorec sshd[6060]: Connection from 77.240.189.2 port 46897
Jul  5 11:56:07 primorec sshd[6060]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:07 primorec sshd[6060]: Invalid user test from 77.240.189.2
Jul  5 11:56:07 primorec sshd[6062]: Connection from 77.240.189.2 port 47014
Jul  5 11:56:08 primorec sshd[6062]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:08 primorec sshd[6062]: Invalid user test from 77.240.189.2
Jul  5 11:56:08 primorec sshd[6064]: Connection from 77.240.189.2 port 47153
Jul  5 11:56:09 primorec sshd[6064]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:09 primorec sshd[6064]: Invalid user test from 77.240.189.2
Jul  5 11:56:09 primorec sshd[6066]: Connection from 77.240.189.2 port 47251
Jul  5 11:56:10 primorec sshd[6066]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:10 primorec sshd[6066]: Invalid user test from 77.240.189.2
Jul  5 11:56:10 primorec sshd[6068]: Connection from 77.240.189.2 port 47364
Jul  5 11:56:10 primorec sshd[6068]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:10 primorec sshd[6068]: Invalid user test from 77.240.189.2
Jul  5 11:56:11 primorec sshd[6070]: Connection from 77.240.189.2 port 47502
Jul  5 11:56:11 primorec sshd[6070]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:11 primorec sshd[6070]: Invalid user test from 77.240.189.2
Jul  5 11:56:12 primorec sshd[6072]: Connection from 77.240.189.2 port 47611
Jul  5 11:56:12 primorec sshd[6072]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:12 primorec sshd[6072]: Invalid user test from 77.240.189.2
Jul  5 11:56:12 primorec sshd[6074]: Connection from 77.240.189.2 port 47719
Jul  5 11:56:13 primorec sshd[6074]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:13 primorec sshd[6074]: Invalid user test from 77.240.189.2
Jul  5 11:56:13 primorec sshd[6076]: Connection from 77.240.189.2 port 47863
Jul  5 11:56:14 primorec sshd[6076]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:14 primorec sshd[6076]: Invalid user test from 77.240.189.2
Jul  5 11:56:14 primorec sshd[6078]: Connection from 77.240.189.2 port 47978
Jul  5 11:56:15 primorec sshd[6078]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:15 primorec sshd[6078]: Invalid user test from 77.240.189.2
Jul  5 11:56:15 primorec sshd[6080]: Connection from 77.240.189.2 port 48079
Jul  5 11:56:16 primorec sshd[6080]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:16 primorec sshd[6080]: Invalid user test from 77.240.189.2
Jul  5 11:56:16 primorec sshd[6082]: Connection from 77.240.189.2 port 48207
Jul  5 11:56:17 primorec sshd[6082]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:17 primorec sshd[6082]: Invalid user test from 77.240.189.2
Jul  5 11:56:17 primorec sshd[6084]: Connection from 77.240.189.2 port 48343
Jul  5 11:56:17 primorec sshd[6084]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:17 primorec sshd[6084]: Invalid user test from 77.240.189.2
Jul  5 11:56:18 primorec sshd[6086]: Connection from 77.240.189.2 port 48451
Jul  5 11:56:18 primorec sshd[6086]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:18 primorec sshd[6086]: Invalid user test from 77.240.189.2
Jul  5 11:56:18 primorec sshd[6088]: Connection from 77.240.189.2 port 48571
Jul  5 11:56:19 primorec sshd[6088]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:19 primorec sshd[6088]: Invalid user test from 77.240.189.2
Jul  5 11:56:19 primorec sshd[6090]: Connection from 77.240.189.2 port 48716
Jul  5 11:56:20 primorec sshd[6090]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:20 primorec sshd[6090]: Invalid user test from 77.240.189.2
Jul  5 11:56:20 primorec sshd[6092]: Connection from 77.240.189.2 port 48838
Jul  5 11:56:21 primorec sshd[6092]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:21 primorec sshd[6092]: Invalid user test from 77.240.189.2
Jul  5 11:56:21 primorec sshd[6094]: Connection from 77.240.189.2 port 48949
Jul  5 11:56:22 primorec sshd[6094]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:22 primorec sshd[6094]: Invalid user test from 77.240.189.2
Jul  5 11:56:22 primorec sshd[6096]: Connection from 77.240.189.2 port 49077
Jul  5 11:56:23 primorec sshd[6096]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:23 primorec sshd[6096]: Invalid user test from 77.240.189.2
Jul  5 11:56:23 primorec sshd[6098]: Connection from 77.240.189.2 port 49193
Jul  5 11:56:24 primorec sshd[6098]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:24 primorec sshd[6098]: Invalid user test from 77.240.189.2
Jul  5 11:56:24 primorec sshd[6100]: Connection from 77.240.189.2 port 49322
Jul  5 11:56:25 primorec sshd[6100]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:25 primorec sshd[6100]: Invalid user test from 77.240.189.2
Jul  5 11:56:25 primorec sshd[6102]: Connection from 77.240.189.2 port 49454
Jul  5 11:56:25 primorec sshd[6102]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:25 primorec sshd[6102]: Invalid user test from 77.240.189.2
Jul  5 11:56:26 primorec sshd[6104]: Connection from 77.240.189.2 port 49750
Jul  5 11:56:28 primorec sshd[6104]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:28 primorec sshd[6104]: Invalid user test1 from 77.240.189.2
Jul  5 11:56:28 primorec sshd[6106]: Connection from 77.240.189.2 port 50214
Jul  5 11:56:29 primorec sshd[6106]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:29 primorec sshd[6106]: Invalid user test1 from 77.240.189.2
Jul  5 11:56:29 primorec sshd[6108]: Connection from 77.240.189.2 port 50446
Jul  5 11:56:31 primorec sshd[6108]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:31 primorec sshd[6108]: Invalid user test2 from 77.240.189.2
Jul  5 11:56:31 primorec sshd[6110]: Connection from 77.240.189.2 port 50840
Jul  5 11:56:33 primorec sshd[6110]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:33 primorec sshd[6110]: Invalid user test2 from 77.240.189.2
Jul  5 11:56:33 primorec sshd[6112]: Connection from 77.240.189.2 port 51102
Jul  5 11:56:34 primorec sshd[6112]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:34 primorec sshd[6112]: Invalid user test3 from 77.240.189.2
Jul  5 11:56:35 primorec sshd[6114]: Connection from 77.240.189.2 port 51417
Jul  5 11:56:36 primorec sshd[6114]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:36 primorec sshd[6114]: Invalid user test4 from 77.240.189.2
Jul  5 11:56:37 primorec sshd[6116]: Connection from 77.240.189.2 port 51791
Jul  5 11:56:38 primorec sshd[6116]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:38 primorec sshd[6116]: Invalid user test3 from 77.240.189.2
Jul  5 11:56:39 primorec sshd[6118]: Connection from 77.240.189.2 port 52125
Jul  5 11:56:40 primorec sshd[6118]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:40 primorec sshd[6118]: Invalid user test5 from 77.240.189.2
Jul  5 11:56:41 primorec sshd[6120]: Connection from 77.240.189.2 port 52483
Jul  5 11:56:42 primorec sshd[6120]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:42 primorec sshd[6120]: Invalid user test5 from 77.240.189.2
Jul  5 11:56:43 primorec sshd[6122]: Connection from 77.240.189.2 port 52826
Jul  5 11:56:45 primorec sshd[6122]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:45 primorec sshd[6122]: Invalid user test6 from 77.240.189.2
Jul  5 11:56:45 primorec sshd[6124]: Connection from 77.240.189.2 port 53173
Jul  5 11:56:46 primorec sshd[6124]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:46 primorec sshd[6124]: Invalid user test6 from 77.240.189.2
Jul  5 11:56:47 primorec sshd[6126]: Connection from 77.240.189.2 port 53494
Jul  5 11:56:49 primorec sshd[6126]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:49 primorec sshd[6126]: Invalid user test7 from 77.240.189.2
Jul  5 11:56:49 primorec sshd[6128]: Connection from 77.240.189.2 port 53872
Jul  5 11:56:51 primorec sshd[6128]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:51 primorec sshd[6128]: Invalid user test7 from 77.240.189.2
Jul  5 11:56:51 primorec sshd[6130]: Connection from 77.240.189.2 port 54200
Jul  5 11:56:53 primorec sshd[6130]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:53 primorec sshd[6130]: Invalid user test8 from 77.240.189.2
Jul  5 11:56:53 primorec sshd[6132]: Connection from 77.240.189.2 port 54579
Jul  5 11:56:55 primorec sshd[6132]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:55 primorec sshd[6132]: Invalid user test8 from 77.240.189.2
Jul  5 11:56:55 primorec sshd[6134]: Connection from 77.240.189.2 port 54909
Jul  5 11:56:57 primorec sshd[6134]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:57 primorec sshd[6134]: Invalid user test9 from 77.240.189.2
Jul  5 11:56:57 primorec sshd[6136]: Connection from 77.240.189.2 port 55274
Jul  5 11:56:58 primorec sshd[6136]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:58 primorec sshd[6136]: Invalid user test9 from 77.240.189.2
Jul  5 11:56:59 primorec sshd[6138]: Connection from 77.240.189.2 port 55577
Jul  5 11:57:00 primorec sshd[6138]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:00 primorec sshd[6138]: Invalid user test0 from 77.240.189.2
Jul  5 11:57:01 primorec sshd[6140]: Connection from 77.240.189.2 port 55931
Jul  5 11:57:02 primorec sshd[6140]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:02 primorec sshd[6140]: Invalid user test0 from 77.240.189.2
Jul  5 11:57:03 primorec sshd[6142]: Connection from 77.240.189.2 port 56251
Jul  5 11:57:04 primorec sshd[6142]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:04 primorec sshd[6142]: Invalid user test4 from 77.240.189.2
Jul  5 11:57:05 primorec sshd[6144]: Connection from 77.240.189.2 port 56617
Jul  5 11:57:06 primorec sshd[6144]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:06 primorec sshd[6144]: Invalid user test111 from 77.240.189.2
Jul  5 11:57:06 primorec sshd[6146]: Connection from 77.240.189.2 port 56964
Jul  5 11:57:08 primorec sshd[6146]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:08 primorec sshd[6146]: Invalid user test112 from 77.240.189.2
Jul  5 11:57:08 primorec sshd[6148]: Connection from 77.240.189.2 port 57289
Jul  5 11:57:10 primorec sshd[6148]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:10 primorec sshd[6148]: Invalid user test113 from 77.240.189.2
Jul  5 11:57:10 primorec sshd[6150]: Connection from 77.240.189.2 port 57622
Jul  5 11:57:12 primorec sshd[6150]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:12 primorec sshd[6150]: Invalid user test999 from 77.240.189.2
Jul  5 11:57:12 primorec sshd[6152]: Connection from 77.240.189.2 port 57973
Jul  5 11:57:14 primorec sshd[6152]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:14 primorec sshd[6152]: Invalid user teston from 77.240.189.2
Jul  5 11:57:14 primorec sshd[6154]: Connection from 77.240.189.2 port 58321
Jul  5 11:57:16 primorec sshd[6154]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:16 primorec sshd[6154]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:17 primorec sshd[6156]: Connection from 77.240.189.2 port 58675
Jul  5 11:57:18 primorec sshd[6156]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:18 primorec sshd[6156]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:19 primorec sshd[6158]: Connection from 77.240.189.2 port 59102
Jul  5 11:57:21 primorec sshd[6158]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:21 primorec sshd[6158]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:21 primorec sshd[6160]: Connection from 77.240.189.2 port 59422
Jul  5 11:57:23 primorec sshd[6160]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:23 primorec sshd[6160]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:23 primorec sshd[6162]: Connection from 77.240.189.2 port 59771
Jul  5 11:57:25 primorec sshd[6162]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:25 primorec sshd[6162]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:25 primorec sshd[6164]: Connection from 77.240.189.2 port 60097
Jul  5 11:57:27 primorec sshd[6164]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:27 primorec sshd[6164]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:27 primorec sshd[6166]: Connection from 77.240.189.2 port 60457
Jul  5 11:57:29 primorec sshd[6166]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:29 primorec sshd[6166]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:29 primorec sshd[6168]: Connection from 77.240.189.2 port 60777
Jul  5 11:57:31 primorec sshd[6168]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:31 primorec sshd[6168]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:32 primorec sshd[6170]: Connection from 77.240.189.2 port 32909
Jul  5 11:57:33 primorec sshd[6170]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:33 primorec sshd[6170]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:34 primorec sshd[6172]: Connection from 77.240.189.2 port 33213
Jul  5 11:57:35 primorec sshd[6172]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:35 primorec sshd[6172]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:36 primorec sshd[6174]: Connection from 77.240.189.2 port 33579
Jul  5 11:57:37 primorec sshd[6174]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:37 primorec sshd[6174]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:38 primorec sshd[6176]: Connection from 77.240.189.2 port 33889
Jul  5 11:57:39 primorec sshd[6176]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:39 primorec sshd[6176]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:40 primorec sshd[6178]: Connection from 77.240.189.2 port 34267
Jul  5 11:57:42 primorec sshd[6178]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:42 primorec sshd[6178]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:42 primorec sshd[6180]: Connection from 77.240.189.2 port 34609
Jul  5 11:57:44 primorec sshd[6180]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:44 primorec sshd[6180]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:44 primorec sshd[6182]: Connection from 77.240.189.2 port 34982
Jul  5 11:57:46 primorec sshd[6182]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:46 primorec sshd[6182]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:46 primorec sshd[6184]: Connection from 77.240.189.2 port 35305
Jul  5 11:57:48 primorec sshd[6184]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:48 primorec sshd[6184]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:48 primorec sshd[6186]: Connection from 77.240.189.2 port 35648
Jul  5 11:57:50 primorec sshd[6186]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:50 primorec sshd[6186]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:50 primorec sshd[6188]: Connection from 77.240.189.2 port 35990
Jul  5 11:57:52 primorec sshd[6188]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:52 primorec sshd[6188]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:52 primorec sshd[6190]: Connection from 77.240.189.2 port 36334
Jul  5 11:57:54 primorec sshd[6190]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:54 primorec sshd[6190]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:54 primorec sshd[6192]: Connection from 77.240.189.2 port 36662
Jul  5 11:57:55 primorec sshd[6192]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:55 primorec sshd[6192]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:56 primorec sshd[6194]: Connection from 77.240.189.2 port 36988
Jul  5 11:57:57 primorec sshd[6194]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:57 primorec sshd[6194]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:58 primorec sshd[6196]: Connection from 77.240.189.2 port 37334
Jul  5 11:57:59 primorec sshd[6196]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:59 primorec sshd[6196]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:00 primorec sshd[6198]: Connection from 77.240.189.2 port 37677
Jul  5 11:58:01 primorec sshd[6198]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:01 primorec sshd[6198]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:02 primorec sshd[6200]: Connection from 77.240.189.2 port 38017
Jul  5 11:58:03 primorec sshd[6200]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:03 primorec sshd[6200]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:03 primorec sshd[6202]: Connection from 77.240.189.2 port 38323
Jul  5 11:58:05 primorec sshd[6202]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:05 primorec sshd[6202]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:05 primorec sshd[6204]: Connection from 77.240.189.2 port 38674
Jul  5 11:58:07 primorec sshd[6204]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:07 primorec sshd[6204]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:08 primorec sshd[6206]: Connection from 77.240.189.2 port 39040
Jul  5 11:58:09 primorec sshd[6206]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:09 primorec sshd[6206]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:09 primorec sshd[6208]: Connection from 77.240.189.2 port 39354
Jul  5 11:58:11 primorec sshd[6208]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:11 primorec sshd[6208]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:11 primorec sshd[6210]: Connection from 77.240.189.2 port 39686
Jul  5 11:58:13 primorec sshd[6210]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:13 primorec sshd[6210]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:13 primorec sshd[6212]: Connection from 77.240.189.2 port 40020
Jul  5 11:58:14 primorec sshd[6212]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:14 primorec sshd[6212]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:15 primorec sshd[6214]: Connection from 77.240.189.2 port 40294
Jul  5 11:58:16 primorec sshd[6214]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:16 primorec sshd[6214]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:17 primorec sshd[6216]: Connection from 77.240.189.2 port 40666
Jul  5 11:58:18 primorec sshd[6216]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:18 primorec sshd[6216]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:18 primorec sshd[6218]: Connection from 77.240.189.2 port 40978
Jul  5 11:58:20 primorec sshd[6218]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:20 primorec sshd[6218]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:20 primorec sshd[6220]: Connection from 77.240.189.2 port 41327
Jul  5 11:58:22 primorec sshd[6220]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:22 primorec sshd[6220]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:23 primorec sshd[6222]: Connection from 77.240.189.2 port 41683
Jul  5 11:58:24 primorec sshd[6222]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:24 primorec sshd[6222]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:24 primorec sshd[6224]: Connection from 77.240.189.2 port 41983
Jul  5 11:58:26 primorec sshd[6224]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:26 primorec sshd[6224]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:26 primorec sshd[6226]: Connection from 77.240.189.2 port 42308
Jul  5 11:58:28 primorec sshd[6226]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:28 primorec sshd[6226]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:28 primorec sshd[6228]: Connection from 77.240.189.2 port 42619
Jul  5 11:58:29 primorec sshd[6228]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:29 primorec sshd[6228]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:30 primorec sshd[6230]: Connection from 77.240.189.2 port 42963
Jul  5 11:58:31 primorec sshd[6230]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:31 primorec sshd[6230]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:32 primorec sshd[6232]: Connection from 77.240.189.2 port 43261
Jul  5 11:58:33 primorec sshd[6232]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:33 primorec sshd[6232]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:34 primorec sshd[6234]: Connection from 77.240.189.2 port 43573
Jul  5 11:58:35 primorec sshd[6234]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:35 primorec sshd[6234]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:36 primorec sshd[6236]: Connection from 77.240.189.2 port 43909
Jul  5 11:58:37 primorec sshd[6236]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:37 primorec sshd[6236]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:37 primorec sshd[6238]: Connection from 77.240.189.2 port 44218
Jul  5 11:58:39 primorec sshd[6238]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:39 primorec sshd[6238]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:39 primorec sshd[6240]: Connection from 77.240.189.2 port 44559
Jul  5 11:58:41 primorec sshd[6240]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:41 primorec sshd[6240]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:41 primorec sshd[6242]: Connection from 77.240.189.2 port 44898
Jul  5 11:58:43 primorec sshd[6242]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:43 primorec sshd[6242]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:44 primorec sshd[6244]: Connection from 77.240.189.2 port 45200
Jul  5 11:58:45 primorec sshd[6244]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:45 primorec sshd[6244]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:45 primorec sshd[6246]: Connection from 77.240.189.2 port 45526
Jul  5 11:58:47 primorec sshd[6246]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:47 primorec sshd[6246]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:47 primorec sshd[6248]: Connection from 77.240.189.2 port 45840
Jul  5 11:58:48 primorec sshd[6248]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:48 primorec sshd[6248]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:49 primorec sshd[6250]: Connection from 77.240.189.2 port 46137
Jul  5 11:58:50 primorec sshd[6250]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:50 primorec sshd[6250]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:51 primorec sshd[6252]: Connection from 77.240.189.2 port 46487
Jul  5 11:58:52 primorec sshd[6252]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:52 primorec sshd[6252]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:53 primorec sshd[6254]: Connection from 77.240.189.2 port 46782
Jul  5 11:58:54 primorec sshd[6254]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:54 primorec sshd[6254]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:54 primorec sshd[6256]: Connection from 77.240.189.2 port 47087
Jul  5 11:58:56 primorec sshd[6256]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:56 primorec sshd[6256]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:56 primorec sshd[6258]: Connection from 77.240.189.2 port 47377
Jul  5 11:58:57 primorec sshd[6258]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:57 primorec sshd[6258]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:58 primorec sshd[6260]: Connection from 77.240.189.2 port 47702
Jul  5 11:58:59 primorec sshd[6260]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:59 primorec sshd[6260]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:00 primorec sshd[6262]: Connection from 77.240.189.2 port 48017
Jul  5 11:59:01 primorec sshd[6262]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:01 primorec sshd[6262]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:01 primorec sshd[6264]: Connection from 77.240.189.2 port 48319
Jul  5 11:59:02 primorec sshd[6264]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:02 primorec sshd[6264]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:03 primorec sshd[6266]: Connection from 77.240.189.2 port 48619
Jul  5 11:59:04 primorec sshd[6266]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:04 primorec sshd[6266]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:05 primorec sshd[6268]: Connection from 77.240.189.2 port 48945
Jul  5 11:59:06 primorec sshd[6268]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:06 primorec sshd[6268]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:06 primorec sshd[6270]: Connection from 77.240.189.2 port 49246
Jul  5 11:59:08 primorec sshd[6270]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:08 primorec sshd[6270]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:08 primorec sshd[6272]: Connection from 77.240.189.2 port 49542
Jul  5 11:59:10 primorec sshd[6272]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:10 primorec sshd[6272]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:10 primorec sshd[6274]: Connection from 77.240.189.2 port 49899
Jul  5 11:59:12 primorec sshd[6274]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:12 primorec sshd[6274]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:12 primorec sshd[6276]: Connection from 77.240.189.2 port 50203
Jul  5 11:59:14 primorec sshd[6276]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:14 primorec sshd[6276]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:14 primorec sshd[6278]: Connection from 77.240.189.2 port 50540
Jul  5 11:59:16 primorec sshd[6278]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:16 primorec sshd[6278]: Invalid user testy from 77.240.189.2
Jul  5 11:59:16 primorec sshd[6280]: Connection from 77.240.189.2 port 50831
Jul  5 11:59:18 primorec sshd[6280]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:18 primorec sshd[6280]: Invalid user user from 77.240.189.2
Jul  5 11:59:18 primorec sshd[6282]: Connection from 77.240.189.2 port 51167
Jul  5 11:59:19 primorec sshd[6282]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:19 primorec sshd[6282]: Invalid user user from 77.240.189.2
Jul  5 11:59:20 primorec sshd[6284]: Connection from 77.240.189.2 port 51452
Jul  5 11:59:21 primorec sshd[6284]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:21 primorec sshd[6284]: Invalid user user from 77.240.189.2
Jul  5 11:59:21 primorec sshd[6286]: Connection from 77.240.189.2 port 51733
Jul  5 11:59:23 primorec sshd[6286]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:23 primorec sshd[6286]: Invalid user user from 77.240.189.2
Jul  5 11:59:23 primorec sshd[6288]: Connection from 77.240.189.2 port 52057
Jul  5 11:59:25 primorec sshd[6288]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:25 primorec sshd[6288]: Invalid user user from 77.240.189.2
Jul  5 11:59:25 primorec sshd[6290]: Connection from 77.240.189.2 port 52345
Jul  5 11:59:26 primorec sshd[6290]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:26 primorec sshd[6290]: Invalid user user from 77.240.189.2
Jul  5 11:59:27 primorec sshd[6292]: Connection from 77.240.189.2 port 52692
Jul  5 11:59:28 primorec sshd[6292]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:28 primorec sshd[6292]: Invalid user user from 77.240.189.2
Jul  5 11:59:28 primorec sshd[6294]: Connection from 77.240.189.2 port 52953
Jul  5 11:59:30 primorec sshd[6294]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:30 primorec sshd[6294]: Invalid user user from 77.240.189.2
Jul  5 11:59:30 primorec sshd[6296]: Connection from 77.240.189.2 port 53260
Jul  5 11:59:32 primorec sshd[6296]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:32 primorec sshd[6296]: Invalid user user from 77.240.189.2
Jul  5 11:59:32 primorec sshd[6298]: Connection from 77.240.189.2 port 53571
Jul  5 11:59:34 primorec sshd[6298]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:34 primorec sshd[6298]: Invalid user user from 77.240.189.2
Jul  5 11:59:34 primorec sshd[6300]: Connection from 77.240.189.2 port 53845
Jul  5 11:59:36 primorec sshd[6300]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:36 primorec sshd[6300]: Invalid user user from 77.240.189.2
Jul  5 11:59:36 primorec sshd[6343]: Connection from 77.240.189.2 port 54203
Jul  5 11:59:37 primorec sshd[6343]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:37 primorec sshd[6343]: Invalid user user from 77.240.189.2
Jul  5 11:59:38 primorec sshd[6353]: Connection from 77.240.189.2 port 54464
Jul  5 11:59:39 primorec sshd[6353]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:39 primorec sshd[6353]: Invalid user user from 77.240.189.2
Jul  5 11:59:39 primorec sshd[6355]: Connection from 77.240.189.2 port 54758
Jul  5 11:59:41 primorec sshd[6355]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:41 primorec sshd[6355]: Invalid user user from 77.240.189.2
Jul  5 11:59:41 primorec sshd[6357]: Connection from 77.240.189.2 port 55096
Jul  5 11:59:43 primorec sshd[6357]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:43 primorec sshd[6357]: Invalid user user from 77.240.189.2
Jul  5 11:59:43 primorec sshd[6359]: Connection from 77.240.189.2 port 55351
Jul  5 11:59:44 primorec sshd[6359]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:44 primorec sshd[6359]: Invalid user user from 77.240.189.2
Jul  5 11:59:45 primorec sshd[6361]: Connection from 77.240.189.2 port 55692
Jul  5 11:59:46 primorec sshd[6361]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:46 primorec sshd[6361]: Invalid user user from 77.240.189.2
Jul  5 11:59:47 primorec sshd[6373]: Connection from 77.240.189.2 port 56007
Jul  5 11:59:48 primorec sshd[6373]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:48 primorec sshd[6373]: Invalid user user from 77.240.189.2
Jul  5 11:59:49 primorec sshd[6377]: Connection from 77.240.189.2 port 56310
Jul  5 11:59:50 primorec sshd[6377]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:50 primorec sshd[6377]: Invalid user user from 77.240.189.2
Jul  5 11:59:50 primorec sshd[6379]: Connection from 77.240.189.2 port 56568
Jul  5 11:59:52 primorec sshd[6379]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:52 primorec sshd[6379]: Invalid user user from 77.240.189.2
Jul  5 11:59:52 primorec sshd[6381]: Connection from 77.240.189.2 port 56905
Jul  5 11:59:53 primorec sshd[6381]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:53 primorec sshd[6381]: Invalid user user from 77.240.189.2
Jul  5 11:59:54 primorec sshd[6383]: Connection from 77.240.189.2 port 57173
Jul  5 11:59:55 primorec sshd[6383]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:55 primorec sshd[6383]: Invalid user user from 77.240.189.2
Jul  5 11:59:55 primorec sshd[6385]: Connection from 77.240.189.2 port 35297
Jul  5 11:59:57 primorec sshd[6385]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:57 primorec sshd[6385]: Invalid user user1 from 77.240.189.2
Jul  5 11:59:57 primorec sshd[6387]: Connection from 77.240.189.2 port 35587
Jul  5 11:59:58 primorec sshd[6387]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:58 primorec sshd[6387]: Invalid user user1 from 77.240.189.2
Jul  5 11:59:59 primorec sshd[6389]: Connection from 77.240.189.2 port 35877
Jul  5 12:00:00 primorec sshd[6389]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:00 primorec sshd[6389]: Invalid user user2 from 77.240.189.2
Jul  5 12:00:01 primorec sshd[6406]: Connection from 77.240.189.2 port 36201
Jul  5 12:00:02 primorec sshd[6406]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:02 primorec sshd[6406]: Invalid user user2 from 77.240.189.2
Jul  5 12:00:02 primorec sshd[6563]: Connection from 77.240.189.2 port 36468
Jul  5 12:00:04 primorec sshd[6563]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:04 primorec sshd[6563]: Invalid user user3 from 77.240.189.2
Jul  5 12:00:04 primorec sshd[6878]: Connection from 77.240.189.2 port 36783
Jul  5 12:00:05 primorec sshd[6878]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:05 primorec sshd[6878]: Invalid user user4 from 77.240.189.2
Jul  5 12:00:06 primorec sshd[6880]: Connection from 77.240.189.2 port 37070
Jul  5 12:00:07 primorec sshd[6880]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:07 primorec sshd[6880]: Invalid user user5 from 77.240.189.2
Jul  5 12:00:07 primorec sshd[6882]: Connection from 77.240.189.2 port 37347
Jul  5 12:00:08 primorec sshd[6882]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:08 primorec sshd[6882]: Invalid user user6 from 77.240.189.2
Jul  5 12:00:09 primorec sshd[6884]: Connection from 77.240.189.2 port 37628
Jul  5 12:00:10 primorec sshd[6884]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:10 primorec sshd[6884]: Invalid user user7 from 77.240.189.2
Jul  5 12:00:11 primorec sshd[6886]: Connection from 77.240.189.2 port 37951
Jul  5 12:00:12 primorec sshd[6886]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:12 primorec sshd[6886]: Invalid user user8 from 77.240.189.2
Jul  5 12:00:12 primorec sshd[6898]: Connection from 77.240.189.2 port 38211
Jul  5 12:00:13 primorec sshd[6898]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:13 primorec sshd[6898]: Invalid user user9 from 77.240.189.2
Jul  5 12:00:14 primorec sshd[6902]: Connection from 77.240.189.2 port 38494
Jul  5 12:00:16 primorec sshd[6902]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:16 primorec sshd[6902]: Invalid user username from 77.240.189.2
Jul  5 12:00:16 primorec sshd[6904]: Connection from 77.240.189.2 port 38816
Jul  5 12:00:17 primorec sshd[6904]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:17 primorec sshd[6904]: Invalid user username from 77.240.189.2
Jul  5 12:00:18 primorec sshd[6906]: Connection from 77.240.189.2 port 39089
Jul  5 12:00:19 primorec sshd[6906]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:19 primorec sshd[6906]: Invalid user users from 77.240.189.2
Jul  5 12:00:19 primorec sshd[6908]: Connection from 77.240.189.2 port 39397
Jul  5 12:00:21 primorec sshd[6908]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:21 primorec sshd[6908]: Invalid user wbe from 77.240.189.2
Jul  5 12:00:21 primorec sshd[6910]: Connection from 77.240.189.2 port 39659
Jul  5 12:00:22 primorec sshd[6910]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:22 primorec sshd[6910]: Invalid user wbe from 77.240.189.2
Jul  5 12:00:23 primorec sshd[6912]: Connection from 77.240.189.2 port 39934
Jul  5 12:00:24 primorec sshd[6912]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:24 primorec sshd[6912]: Invalid user web from 77.240.189.2
Jul  5 12:00:25 primorec sshd[6914]: Connection from 77.240.189.2 port 40263
Jul  5 12:00:26 primorec sshd[6914]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:26 primorec sshd[6914]: Invalid user web from 77.240.189.2
Jul  5 12:00:26 primorec sshd[6917]: Connection from 77.240.189.2 port 40526
Jul  5 12:00:28 primorec sshd[6917]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:28 primorec sshd[6917]: Invalid user web from 77.240.189.2
Jul  5 12:00:28 primorec sshd[6919]: Connection from 77.240.189.2 port 40844
Jul  5 12:00:30 primorec sshd[6919]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:30 primorec sshd[6919]: Invalid user web from 77.240.189.2
Jul  5 12:00:30 primorec sshd[6921]: Connection from 77.240.189.2 port 41126
Jul  5 12:00:31 primorec sshd[6921]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:31 primorec sshd[6921]: Invalid user web from 77.240.189.2
Jul  5 12:00:32 primorec sshd[6923]: Connection from 77.240.189.2 port 41383
Jul  5 12:00:33 primorec sshd[6923]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:33 primorec sshd[6923]: Invalid user web from 77.240.189.2
Jul  5 12:00:34 primorec sshd[6925]: Connection from 77.240.189.2 port 41713
Jul  5 12:00:35 primorec sshd[6925]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:35 primorec sshd[6925]: Invalid user web from 77.240.189.2
Jul  5 12:00:35 primorec sshd[6927]: Connection from 77.240.189.2 port 41985
Jul  5 12:00:37 primorec sshd[6927]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:37 primorec sshd[6927]: Invalid user web from 77.240.189.2
Jul  5 12:00:37 primorec sshd[6929]: Connection from 77.240.189.2 port 42299
Jul  5 12:00:39 primorec sshd[6929]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:39 primorec sshd[6929]: Invalid user web from 77.240.189.2
Jul  5 12:00:39 primorec sshd[6931]: Connection from 77.240.189.2 port 42561
Jul  5 12:00:40 primorec sshd[6931]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:40 primorec sshd[6931]: Invalid user web from 77.240.189.2
Jul  5 12:00:40 primorec sshd[6933]: Connection from 77.240.189.2 port 42827
Jul  5 12:00:42 primorec sshd[6933]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:42 primorec sshd[6933]: Invalid user web from 77.240.189.2
Jul  5 12:00:42 primorec sshd[6935]: Connection from 77.240.189.2 port 43144
Jul  5 12:00:43 primorec sshd[6935]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:43 primorec sshd[6935]: Invalid user web from 77.240.189.2
Jul  5 12:00:44 primorec sshd[6937]: Connection from 77.240.189.2 port 43389
Jul  5 12:00:45 primorec sshd[6937]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:45 primorec sshd[6937]: Invalid user web from 77.240.189.2
Jul  5 12:00:45 primorec sshd[6939]: Connection from 77.240.189.2 port 43663
Jul  5 12:00:47 primorec sshd[6939]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:47 primorec sshd[6939]: Invalid user web from 77.240.189.2
Jul  5 12:00:47 primorec sshd[6941]: Connection from 77.240.189.2 port 43971
Jul  5 12:00:48 primorec sshd[6941]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:48 primorec sshd[6941]: Invalid user web from 77.240.189.2
Jul  5 12:00:49 primorec sshd[6943]: Connection from 77.240.189.2 port 44247
Jul  5 12:00:50 primorec sshd[6943]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:50 primorec sshd[6943]: Invalid user web from 77.240.189.2
Jul  5 12:00:50 primorec sshd[6945]: Connection from 77.240.189.2 port 44496
Jul  5 12:00:51 primorec sshd[6945]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:51 primorec sshd[6945]: Invalid user web from 77.240.189.2
Jul  5 12:00:52 primorec sshd[6952]: Connection from 77.240.189.2 port 44755
Jul  5 12:00:53 primorec sshd[6952]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:53 primorec sshd[6952]: Invalid user web from 77.240.189.2
Jul  5 12:00:53 primorec sshd[6959]: Connection from 77.240.189.2 port 45048
Jul  5 12:00:55 primorec sshd[6959]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:55 primorec sshd[6959]: Invalid user web from 77.240.189.2
Jul  5 12:00:55 primorec sshd[6962]: Connection from 77.240.189.2 port 45319
Jul  5 12:00:56 primorec sshd[6962]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:56 primorec sshd[6962]: Invalid user web from 77.240.189.2
Jul  5 12:00:56 primorec sshd[6964]: Connection from 77.240.189.2 port 45527
Jul  5 12:00:57 primorec sshd[6964]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:57 primorec sshd[6964]: Invalid user web from 77.240.189.2
Jul  5 12:00:58 primorec sshd[6966]: Connection from 77.240.189.2 port 45826
Jul  5 12:00:59 primorec sshd[6966]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:59 primorec sshd[6966]: Invalid user web from 77.240.189.2
Jul  5 12:01:00 primorec sshd[6968]: Connection from 77.240.189.2 port 46100
Jul  5 12:01:01 primorec sshd[6968]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:01 primorec sshd[6968]: Invalid user web from 77.240.189.2
Jul  5 12:01:01 primorec sshd[6970]: Connection from 77.240.189.2 port 46371
Jul  5 12:01:02 primorec sshd[6970]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:02 primorec sshd[6970]: Invalid user web from 77.240.189.2
Jul  5 12:01:02 primorec sshd[6972]: Connection from 77.240.189.2 port 46609
Jul  5 12:01:03 primorec sshd[6972]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:03 primorec sshd[6972]: Invalid user web from 77.240.189.2
Jul  5 12:01:04 primorec sshd[6974]: Connection from 77.240.189.2 port 46856
Jul  5 12:01:05 primorec sshd[6974]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:05 primorec sshd[6974]: Invalid user web from 77.240.189.2
Jul  5 12:01:05 primorec sshd[6976]: Connection from 77.240.189.2 port 47141
Jul  5 12:01:06 primorec sshd[6976]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:06 primorec sshd[6976]: Invalid user web from 77.240.189.2
Jul  5 12:01:06 primorec sshd[6978]: Connection from 77.240.189.2 port 47352
Jul  5 12:01:07 primorec sshd[6978]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:07 primorec sshd[6978]: Invalid user web from 77.240.189.2
Jul  5 12:01:08 primorec sshd[6980]: Connection from 77.240.189.2 port 47576
Jul  5 12:01:09 primorec sshd[6980]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:09 primorec sshd[6980]: Invalid user web from 77.240.189.2
Jul  5 12:01:09 primorec sshd[6982]: Connection from 77.240.189.2 port 47884
Jul  5 12:01:11 primorec sshd[6982]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:11 primorec sshd[6982]: Invalid user web from 77.240.189.2
```

I use pub key for authentication not password but i use standard port 22 for ssh.

---

### Post by rookcifer on 2009-07-06
Just some clown trying to brute force your password (which you wisely do not use).  There's nothing to worry about.  If you don't like the attempts, then change the port from 22 to something else.

---

### Post by wojox on 2009-07-06
Is that your ip address?

Do you use a router?

If that is your ip then you need to add it to your host file.

---

### Post by triangleSLO on 2009-07-06
77.240.189.2 is attackers IP
I have router

---

### Post by wojox on 2009-07-06
Well it's someone in the Czech Republic running

Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at 77.240.189.2 Port 80

They left there server signature on.

Dunno???

---

### Post by triangleSLO on 2009-07-06
If you tell me where to look i can look for it :)

---

### Post by wojox on 2009-07-06
Look for what?

---

### Post by triangleSLO on 2009-07-06
I thought i should look for server signatures :D

---

### Post by wojox on 2009-07-06
I'm still not sure what you're asking?

If you enter [http://77.240.189.2](http://77.240.189.2)

It will bring you to that computer and show you the server signature.

Or do you want to know how to turn it off because it is your ip address?

---

### Post by scorp123 on 2009-07-06
> **triangleSLO said:**
> I am new to ssh and maybe a little too paranoid. Should i be worried by this log? If you want to get rid of that idiot: Install "denyhosts". It will auto-block any wannabe intruder after a pre-configured amount of failed login attempts. And voila .... peace. No more trouble from that moron.

Please see here for more details:
[http://ubuntuforums.org/showpost.php?p=7550539&postcount=10](http://ubuntuforums.org/showpost.php?p=7550539&postcount=10)

---

### Post by triangleSLO on 2009-07-06
@wojox nevrmind :)

I'll try that scorp 123

---

### Post by sasho_zl on 2009-07-06
Or you can just type the **whois **command with that ip and you will see the information of his service provider and then write one  email to him and explain about the attacks. The ISP could be cooperative. And also don't forget to add this ip adress to the hosts.deny file just in case.

---

### Post by scorp123 on 2009-07-06
> **sasho_zl said:**
> Or you can just type the **whois **command with that ip and you will see the information of his service provider and then write one  email to him  Chances are that the guy is a spammer too. He will happily accept your e-mail address .... So you shouldn't be providing it to him.

> **sasho_zl said:**
>  and explain about the attacks. Chances are he won't care.

> **sasho_zl said:**
>  The ISP could be cooperative.  Could, yes. But we're talking about Eastern Europe here, the "far East" of the EU. Maybe they are indeed cooperative ... or maybe they don't give a four-letter-word about it. Why bother? Block that guy, voila. Peace.

> **sasho_zl said:**
>  And also don't forget to add this ip adress to the hosts.deny file just in case. That's what "denyhosts" is for so this happens auto-magically. :)

---

### Post by triangleSLO on 2009-07-17
Can you tell me if he got access to my computer?
I checked ip and its quite famous. I dont see any access denied messages or anything :/

```
Jul 12 20:42:09 primorec sshd[22674]: Connection from 61.129.60.23 port 60911
Jul 12 20:42:17 primorec sshd[22676]: Connection from 61.129.60.23 port 33248
Jul 12 20:42:25 primorec sshd[22678]: Connection from 61.129.60.23 port 33823
Jul 12 20:42:32 primorec sshd[22680]: Connection from 61.129.60.23 port 34409
Jul 12 20:42:40 primorec sshd[22682]: Connection from 61.129.60.23 port 34955
Jul 12 20:42:48 primorec sshd[22684]: Connection from 61.129.60.23 port 35490
Jul 12 20:42:56 primorec sshd[22686]: Connection from 61.129.60.23 port 36037
Jul 12 20:43:04 primorec sshd[22688]: Connection from 61.129.60.23 port 36569
Jul 12 20:43:12 primorec sshd[22690]: Connection from 61.129.60.23 port 37101
Jul 12 20:43:19 primorec sshd[22692]: Connection from 61.129.60.23 port 37665
Jul 12 20:43:27 primorec sshd[22694]: Connection from 61.129.60.23 port 38175
Jul 12 20:43:35 primorec sshd[22696]: Connection from 61.129.60.23 port 38713
Jul 12 20:43:43 primorec sshd[22698]: Connection from 61.129.60.23 port 39257
Jul 12 20:43:51 primorec sshd[22700]: Connection from 61.129.60.23 port 39803
Jul 12 20:43:59 primorec sshd[22702]: Connection from 61.129.60.23 port 40327
Jul 12 20:44:06 primorec sshd[22704]: Connection from 61.129.60.23 port 40884
Jul 12 20:44:14 primorec sshd[22706]: Connection from 61.129.60.23 port 41417
Jul 12 20:44:22 primorec sshd[22708]: Connection from 61.129.60.23 port 41969
Jul 12 20:44:30 primorec sshd[22710]: Connection from 61.129.60.23 port 60195
Jul 12 20:44:38 primorec sshd[22712]: Connection from 61.129.60.23 port 60755
Jul 12 20:44:46 primorec sshd[22714]: Connection from 61.129.60.23 port 33085
Jul 12 20:44:53 primorec sshd[22716]: Connection from 61.129.60.23 port 33641
Jul 12 20:45:01 primorec sshd[22718]: Connection from 61.129.60.23 port 34193
Jul 12 20:45:09 primorec sshd[22720]: Connection from 61.129.60.23 port 34720
Jul 12 20:45:17 primorec sshd[22722]: Connection from 61.129.60.23 port 35279
Jul 12 20:45:25 primorec sshd[22724]: Connection from 61.129.60.23 port 35800
Jul 12 20:45:32 primorec sshd[22726]: Connection from 61.129.60.23 port 36340
Jul 12 20:45:40 primorec sshd[22728]: Connection from 61.129.60.23 port 36870
Jul 12 20:45:48 primorec sshd[22730]: Connection from 61.129.60.23 port 37411
Jul 12 20:45:56 primorec sshd[22732]: Connection from 61.129.60.23 port 37965
Jul 12 20:46:04 primorec sshd[22734]: Connection from 61.129.60.23 port 38513
Jul 12 21:38:34 primorec sshd[23793]: Connection from 173.45.72.186 port 43576
Jul 12 21:38:36 primorec sshd[23795]: Connection from 173.45.72.186 port 43726
Jul 12 21:38:37 primorec sshd[23797]: Connection from 173.45.72.186 port 43887

```

---

### Post by 89vision on 2009-07-17
My guess is that it is a compromised box running scripts at random IP addresses.  I've noticed similar things on some outward facing servers I have.

---

### Post by ronaldprettyman on 2009-07-17
> **triangleSLO said:**
> I am new to ssh and maybe a little too paranoid. Should i be worried by this log?
```
Jul  5 11:39:48 primorec sshd[5093]: Connection from 77.240.189.2 port 49746
Jul  5 11:39:48 primorec sshd[5093]: Did not receive identification string from 77.240.189.2
Jul  5 11:55:53 primorec sshd[6028]: Connection from 77.240.189.2 port 45031
Jul  5 11:55:54 primorec sshd[6028]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:54 primorec sshd[6028]: Invalid user test from 77.240.189.2
Jul  5 11:55:54 primorec sshd[6030]: Connection from 77.240.189.2 port 45141
Jul  5 11:55:55 primorec sshd[6030]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:55 primorec sshd[6030]: Invalid user test from 77.240.189.2
Jul  5 11:55:55 primorec sshd[6032]: Connection from 77.240.189.2 port 45273
Jul  5 11:55:56 primorec sshd[6032]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:56 primorec sshd[6032]: Invalid user test from 77.240.189.2
Jul  5 11:55:56 primorec sshd[6034]: Connection from 77.240.189.2 port 45403
Jul  5 11:55:57 primorec sshd[6034]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:57 primorec sshd[6034]: Invalid user test from 77.240.189.2
Jul  5 11:55:57 primorec sshd[6036]: Connection from 77.240.189.2 port 45520
Jul  5 11:55:57 primorec sshd[6036]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:57 primorec sshd[6036]: Invalid user test from 77.240.189.2
Jul  5 11:55:58 primorec sshd[6038]: Connection from 77.240.189.2 port 45634
Jul  5 11:55:58 primorec sshd[6038]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:58 primorec sshd[6038]: Invalid user test from 77.240.189.2
Jul  5 11:55:58 primorec sshd[6040]: Connection from 77.240.189.2 port 45765
Jul  5 11:55:59 primorec sshd[6040]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:55:59 primorec sshd[6040]: Invalid user test from 77.240.189.2
Jul  5 11:55:59 primorec sshd[6042]: Connection from 77.240.189.2 port 45879
Jul  5 11:56:00 primorec sshd[6042]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:00 primorec sshd[6042]: Invalid user test from 77.240.189.2
Jul  5 11:56:00 primorec sshd[6044]: Connection from 77.240.189.2 port 45980
Jul  5 11:56:01 primorec sshd[6044]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:01 primorec sshd[6044]: Invalid user test from 77.240.189.2
Jul  5 11:56:01 primorec sshd[6046]: Connection from 77.240.189.2 port 46101
Jul  5 11:56:01 primorec sshd[6046]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:01 primorec sshd[6046]: Invalid user test from 77.240.189.2
Jul  5 11:56:02 primorec sshd[6048]: Connection from 77.240.189.2 port 46224
Jul  5 11:56:02 primorec sshd[6048]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:02 primorec sshd[6048]: Invalid user test from 77.240.189.2
Jul  5 11:56:02 primorec sshd[6050]: Connection from 77.240.189.2 port 46317
Jul  5 11:56:03 primorec sshd[6050]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:03 primorec sshd[6050]: Invalid user test from 77.240.189.2
Jul  5 11:56:03 primorec sshd[6052]: Connection from 77.240.189.2 port 46433
Jul  5 11:56:04 primorec sshd[6052]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:04 primorec sshd[6052]: Invalid user test from 77.240.189.2
Jul  5 11:56:04 primorec sshd[6054]: Connection from 77.240.189.2 port 46535
Jul  5 11:56:05 primorec sshd[6054]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:05 primorec sshd[6054]: Invalid user test from 77.240.189.2
Jul  5 11:56:05 primorec sshd[6056]: Connection from 77.240.189.2 port 46674
Jul  5 11:56:06 primorec sshd[6056]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:06 primorec sshd[6056]: Invalid user test from 77.240.189.2
Jul  5 11:56:06 primorec sshd[6058]: Connection from 77.240.189.2 port 46772
Jul  5 11:56:06 primorec sshd[6058]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:06 primorec sshd[6058]: Invalid user test from 77.240.189.2
Jul  5 11:56:07 primorec sshd[6060]: Connection from 77.240.189.2 port 46897
Jul  5 11:56:07 primorec sshd[6060]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:07 primorec sshd[6060]: Invalid user test from 77.240.189.2
Jul  5 11:56:07 primorec sshd[6062]: Connection from 77.240.189.2 port 47014
Jul  5 11:56:08 primorec sshd[6062]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:08 primorec sshd[6062]: Invalid user test from 77.240.189.2
Jul  5 11:56:08 primorec sshd[6064]: Connection from 77.240.189.2 port 47153
Jul  5 11:56:09 primorec sshd[6064]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:09 primorec sshd[6064]: Invalid user test from 77.240.189.2
Jul  5 11:56:09 primorec sshd[6066]: Connection from 77.240.189.2 port 47251
Jul  5 11:56:10 primorec sshd[6066]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:10 primorec sshd[6066]: Invalid user test from 77.240.189.2
Jul  5 11:56:10 primorec sshd[6068]: Connection from 77.240.189.2 port 47364
Jul  5 11:56:10 primorec sshd[6068]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:10 primorec sshd[6068]: Invalid user test from 77.240.189.2
Jul  5 11:56:11 primorec sshd[6070]: Connection from 77.240.189.2 port 47502
Jul  5 11:56:11 primorec sshd[6070]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:11 primorec sshd[6070]: Invalid user test from 77.240.189.2
Jul  5 11:56:12 primorec sshd[6072]: Connection from 77.240.189.2 port 47611
Jul  5 11:56:12 primorec sshd[6072]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:12 primorec sshd[6072]: Invalid user test from 77.240.189.2
Jul  5 11:56:12 primorec sshd[6074]: Connection from 77.240.189.2 port 47719
Jul  5 11:56:13 primorec sshd[6074]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:13 primorec sshd[6074]: Invalid user test from 77.240.189.2
Jul  5 11:56:13 primorec sshd[6076]: Connection from 77.240.189.2 port 47863
Jul  5 11:56:14 primorec sshd[6076]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:14 primorec sshd[6076]: Invalid user test from 77.240.189.2
Jul  5 11:56:14 primorec sshd[6078]: Connection from 77.240.189.2 port 47978
Jul  5 11:56:15 primorec sshd[6078]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:15 primorec sshd[6078]: Invalid user test from 77.240.189.2
Jul  5 11:56:15 primorec sshd[6080]: Connection from 77.240.189.2 port 48079
Jul  5 11:56:16 primorec sshd[6080]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:16 primorec sshd[6080]: Invalid user test from 77.240.189.2
Jul  5 11:56:16 primorec sshd[6082]: Connection from 77.240.189.2 port 48207
Jul  5 11:56:17 primorec sshd[6082]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:17 primorec sshd[6082]: Invalid user test from 77.240.189.2
Jul  5 11:56:17 primorec sshd[6084]: Connection from 77.240.189.2 port 48343
Jul  5 11:56:17 primorec sshd[6084]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:17 primorec sshd[6084]: Invalid user test from 77.240.189.2
Jul  5 11:56:18 primorec sshd[6086]: Connection from 77.240.189.2 port 48451
Jul  5 11:56:18 primorec sshd[6086]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:18 primorec sshd[6086]: Invalid user test from 77.240.189.2
Jul  5 11:56:18 primorec sshd[6088]: Connection from 77.240.189.2 port 48571
Jul  5 11:56:19 primorec sshd[6088]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:19 primorec sshd[6088]: Invalid user test from 77.240.189.2
Jul  5 11:56:19 primorec sshd[6090]: Connection from 77.240.189.2 port 48716
Jul  5 11:56:20 primorec sshd[6090]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:20 primorec sshd[6090]: Invalid user test from 77.240.189.2
Jul  5 11:56:20 primorec sshd[6092]: Connection from 77.240.189.2 port 48838
Jul  5 11:56:21 primorec sshd[6092]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:21 primorec sshd[6092]: Invalid user test from 77.240.189.2
Jul  5 11:56:21 primorec sshd[6094]: Connection from 77.240.189.2 port 48949
Jul  5 11:56:22 primorec sshd[6094]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:22 primorec sshd[6094]: Invalid user test from 77.240.189.2
Jul  5 11:56:22 primorec sshd[6096]: Connection from 77.240.189.2 port 49077
Jul  5 11:56:23 primorec sshd[6096]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:23 primorec sshd[6096]: Invalid user test from 77.240.189.2
Jul  5 11:56:23 primorec sshd[6098]: Connection from 77.240.189.2 port 49193
Jul  5 11:56:24 primorec sshd[6098]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:24 primorec sshd[6098]: Invalid user test from 77.240.189.2
Jul  5 11:56:24 primorec sshd[6100]: Connection from 77.240.189.2 port 49322
Jul  5 11:56:25 primorec sshd[6100]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:25 primorec sshd[6100]: Invalid user test from 77.240.189.2
Jul  5 11:56:25 primorec sshd[6102]: Connection from 77.240.189.2 port 49454
Jul  5 11:56:25 primorec sshd[6102]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:25 primorec sshd[6102]: Invalid user test from 77.240.189.2
Jul  5 11:56:26 primorec sshd[6104]: Connection from 77.240.189.2 port 49750
Jul  5 11:56:28 primorec sshd[6104]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:28 primorec sshd[6104]: Invalid user test1 from 77.240.189.2
Jul  5 11:56:28 primorec sshd[6106]: Connection from 77.240.189.2 port 50214
Jul  5 11:56:29 primorec sshd[6106]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:29 primorec sshd[6106]: Invalid user test1 from 77.240.189.2
Jul  5 11:56:29 primorec sshd[6108]: Connection from 77.240.189.2 port 50446
Jul  5 11:56:31 primorec sshd[6108]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:31 primorec sshd[6108]: Invalid user test2 from 77.240.189.2
Jul  5 11:56:31 primorec sshd[6110]: Connection from 77.240.189.2 port 50840
Jul  5 11:56:33 primorec sshd[6110]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:33 primorec sshd[6110]: Invalid user test2 from 77.240.189.2
Jul  5 11:56:33 primorec sshd[6112]: Connection from 77.240.189.2 port 51102
Jul  5 11:56:34 primorec sshd[6112]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:34 primorec sshd[6112]: Invalid user test3 from 77.240.189.2
Jul  5 11:56:35 primorec sshd[6114]: Connection from 77.240.189.2 port 51417
Jul  5 11:56:36 primorec sshd[6114]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:36 primorec sshd[6114]: Invalid user test4 from 77.240.189.2
Jul  5 11:56:37 primorec sshd[6116]: Connection from 77.240.189.2 port 51791
Jul  5 11:56:38 primorec sshd[6116]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:38 primorec sshd[6116]: Invalid user test3 from 77.240.189.2
Jul  5 11:56:39 primorec sshd[6118]: Connection from 77.240.189.2 port 52125
Jul  5 11:56:40 primorec sshd[6118]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:40 primorec sshd[6118]: Invalid user test5 from 77.240.189.2
Jul  5 11:56:41 primorec sshd[6120]: Connection from 77.240.189.2 port 52483
Jul  5 11:56:42 primorec sshd[6120]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:42 primorec sshd[6120]: Invalid user test5 from 77.240.189.2
Jul  5 11:56:43 primorec sshd[6122]: Connection from 77.240.189.2 port 52826
Jul  5 11:56:45 primorec sshd[6122]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:45 primorec sshd[6122]: Invalid user test6 from 77.240.189.2
Jul  5 11:56:45 primorec sshd[6124]: Connection from 77.240.189.2 port 53173
Jul  5 11:56:46 primorec sshd[6124]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:46 primorec sshd[6124]: Invalid user test6 from 77.240.189.2
Jul  5 11:56:47 primorec sshd[6126]: Connection from 77.240.189.2 port 53494
Jul  5 11:56:49 primorec sshd[6126]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:49 primorec sshd[6126]: Invalid user test7 from 77.240.189.2
Jul  5 11:56:49 primorec sshd[6128]: Connection from 77.240.189.2 port 53872
Jul  5 11:56:51 primorec sshd[6128]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:51 primorec sshd[6128]: Invalid user test7 from 77.240.189.2
Jul  5 11:56:51 primorec sshd[6130]: Connection from 77.240.189.2 port 54200
Jul  5 11:56:53 primorec sshd[6130]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:53 primorec sshd[6130]: Invalid user test8 from 77.240.189.2
Jul  5 11:56:53 primorec sshd[6132]: Connection from 77.240.189.2 port 54579
Jul  5 11:56:55 primorec sshd[6132]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:55 primorec sshd[6132]: Invalid user test8 from 77.240.189.2
Jul  5 11:56:55 primorec sshd[6134]: Connection from 77.240.189.2 port 54909
Jul  5 11:56:57 primorec sshd[6134]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:57 primorec sshd[6134]: Invalid user test9 from 77.240.189.2
Jul  5 11:56:57 primorec sshd[6136]: Connection from 77.240.189.2 port 55274
Jul  5 11:56:58 primorec sshd[6136]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:56:58 primorec sshd[6136]: Invalid user test9 from 77.240.189.2
Jul  5 11:56:59 primorec sshd[6138]: Connection from 77.240.189.2 port 55577
Jul  5 11:57:00 primorec sshd[6138]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:00 primorec sshd[6138]: Invalid user test0 from 77.240.189.2
Jul  5 11:57:01 primorec sshd[6140]: Connection from 77.240.189.2 port 55931
Jul  5 11:57:02 primorec sshd[6140]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:02 primorec sshd[6140]: Invalid user test0 from 77.240.189.2
Jul  5 11:57:03 primorec sshd[6142]: Connection from 77.240.189.2 port 56251
Jul  5 11:57:04 primorec sshd[6142]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:04 primorec sshd[6142]: Invalid user test4 from 77.240.189.2
Jul  5 11:57:05 primorec sshd[6144]: Connection from 77.240.189.2 port 56617
Jul  5 11:57:06 primorec sshd[6144]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:06 primorec sshd[6144]: Invalid user test111 from 77.240.189.2
Jul  5 11:57:06 primorec sshd[6146]: Connection from 77.240.189.2 port 56964
Jul  5 11:57:08 primorec sshd[6146]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:08 primorec sshd[6146]: Invalid user test112 from 77.240.189.2
Jul  5 11:57:08 primorec sshd[6148]: Connection from 77.240.189.2 port 57289
Jul  5 11:57:10 primorec sshd[6148]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:10 primorec sshd[6148]: Invalid user test113 from 77.240.189.2
Jul  5 11:57:10 primorec sshd[6150]: Connection from 77.240.189.2 port 57622
Jul  5 11:57:12 primorec sshd[6150]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:12 primorec sshd[6150]: Invalid user test999 from 77.240.189.2
Jul  5 11:57:12 primorec sshd[6152]: Connection from 77.240.189.2 port 57973
Jul  5 11:57:14 primorec sshd[6152]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:14 primorec sshd[6152]: Invalid user teston from 77.240.189.2
Jul  5 11:57:14 primorec sshd[6154]: Connection from 77.240.189.2 port 58321
Jul  5 11:57:16 primorec sshd[6154]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:16 primorec sshd[6154]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:17 primorec sshd[6156]: Connection from 77.240.189.2 port 58675
Jul  5 11:57:18 primorec sshd[6156]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:18 primorec sshd[6156]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:19 primorec sshd[6158]: Connection from 77.240.189.2 port 59102
Jul  5 11:57:21 primorec sshd[6158]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:21 primorec sshd[6158]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:21 primorec sshd[6160]: Connection from 77.240.189.2 port 59422
Jul  5 11:57:23 primorec sshd[6160]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:23 primorec sshd[6160]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:23 primorec sshd[6162]: Connection from 77.240.189.2 port 59771
Jul  5 11:57:25 primorec sshd[6162]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:25 primorec sshd[6162]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:25 primorec sshd[6164]: Connection from 77.240.189.2 port 60097
Jul  5 11:57:27 primorec sshd[6164]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:27 primorec sshd[6164]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:27 primorec sshd[6166]: Connection from 77.240.189.2 port 60457
Jul  5 11:57:29 primorec sshd[6166]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:29 primorec sshd[6166]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:29 primorec sshd[6168]: Connection from 77.240.189.2 port 60777
Jul  5 11:57:31 primorec sshd[6168]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:31 primorec sshd[6168]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:32 primorec sshd[6170]: Connection from 77.240.189.2 port 32909
Jul  5 11:57:33 primorec sshd[6170]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:33 primorec sshd[6170]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:34 primorec sshd[6172]: Connection from 77.240.189.2 port 33213
Jul  5 11:57:35 primorec sshd[6172]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:35 primorec sshd[6172]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:36 primorec sshd[6174]: Connection from 77.240.189.2 port 33579
Jul  5 11:57:37 primorec sshd[6174]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:37 primorec sshd[6174]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:38 primorec sshd[6176]: Connection from 77.240.189.2 port 33889
Jul  5 11:57:39 primorec sshd[6176]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:39 primorec sshd[6176]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:40 primorec sshd[6178]: Connection from 77.240.189.2 port 34267
Jul  5 11:57:42 primorec sshd[6178]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:42 primorec sshd[6178]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:42 primorec sshd[6180]: Connection from 77.240.189.2 port 34609
Jul  5 11:57:44 primorec sshd[6180]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:44 primorec sshd[6180]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:44 primorec sshd[6182]: Connection from 77.240.189.2 port 34982
Jul  5 11:57:46 primorec sshd[6182]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:46 primorec sshd[6182]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:46 primorec sshd[6184]: Connection from 77.240.189.2 port 35305
Jul  5 11:57:48 primorec sshd[6184]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:48 primorec sshd[6184]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:48 primorec sshd[6186]: Connection from 77.240.189.2 port 35648
Jul  5 11:57:50 primorec sshd[6186]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:50 primorec sshd[6186]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:50 primorec sshd[6188]: Connection from 77.240.189.2 port 35990
Jul  5 11:57:52 primorec sshd[6188]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:52 primorec sshd[6188]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:52 primorec sshd[6190]: Connection from 77.240.189.2 port 36334
Jul  5 11:57:54 primorec sshd[6190]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:54 primorec sshd[6190]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:54 primorec sshd[6192]: Connection from 77.240.189.2 port 36662
Jul  5 11:57:55 primorec sshd[6192]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:55 primorec sshd[6192]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:56 primorec sshd[6194]: Connection from 77.240.189.2 port 36988
Jul  5 11:57:57 primorec sshd[6194]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:57 primorec sshd[6194]: Invalid user testuser from 77.240.189.2
Jul  5 11:57:58 primorec sshd[6196]: Connection from 77.240.189.2 port 37334
Jul  5 11:57:59 primorec sshd[6196]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:57:59 primorec sshd[6196]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:00 primorec sshd[6198]: Connection from 77.240.189.2 port 37677
Jul  5 11:58:01 primorec sshd[6198]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:01 primorec sshd[6198]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:02 primorec sshd[6200]: Connection from 77.240.189.2 port 38017
Jul  5 11:58:03 primorec sshd[6200]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:03 primorec sshd[6200]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:03 primorec sshd[6202]: Connection from 77.240.189.2 port 38323
Jul  5 11:58:05 primorec sshd[6202]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:05 primorec sshd[6202]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:05 primorec sshd[6204]: Connection from 77.240.189.2 port 38674
Jul  5 11:58:07 primorec sshd[6204]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:07 primorec sshd[6204]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:08 primorec sshd[6206]: Connection from 77.240.189.2 port 39040
Jul  5 11:58:09 primorec sshd[6206]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:09 primorec sshd[6206]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:09 primorec sshd[6208]: Connection from 77.240.189.2 port 39354
Jul  5 11:58:11 primorec sshd[6208]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:11 primorec sshd[6208]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:11 primorec sshd[6210]: Connection from 77.240.189.2 port 39686
Jul  5 11:58:13 primorec sshd[6210]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:13 primorec sshd[6210]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:13 primorec sshd[6212]: Connection from 77.240.189.2 port 40020
Jul  5 11:58:14 primorec sshd[6212]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:14 primorec sshd[6212]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:15 primorec sshd[6214]: Connection from 77.240.189.2 port 40294
Jul  5 11:58:16 primorec sshd[6214]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:16 primorec sshd[6214]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:17 primorec sshd[6216]: Connection from 77.240.189.2 port 40666
Jul  5 11:58:18 primorec sshd[6216]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:18 primorec sshd[6216]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:18 primorec sshd[6218]: Connection from 77.240.189.2 port 40978
Jul  5 11:58:20 primorec sshd[6218]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:20 primorec sshd[6218]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:20 primorec sshd[6220]: Connection from 77.240.189.2 port 41327
Jul  5 11:58:22 primorec sshd[6220]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:22 primorec sshd[6220]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:23 primorec sshd[6222]: Connection from 77.240.189.2 port 41683
Jul  5 11:58:24 primorec sshd[6222]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:24 primorec sshd[6222]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:24 primorec sshd[6224]: Connection from 77.240.189.2 port 41983
Jul  5 11:58:26 primorec sshd[6224]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:26 primorec sshd[6224]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:26 primorec sshd[6226]: Connection from 77.240.189.2 port 42308
Jul  5 11:58:28 primorec sshd[6226]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:28 primorec sshd[6226]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:28 primorec sshd[6228]: Connection from 77.240.189.2 port 42619
Jul  5 11:58:29 primorec sshd[6228]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:29 primorec sshd[6228]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:30 primorec sshd[6230]: Connection from 77.240.189.2 port 42963
Jul  5 11:58:31 primorec sshd[6230]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:31 primorec sshd[6230]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:32 primorec sshd[6232]: Connection from 77.240.189.2 port 43261
Jul  5 11:58:33 primorec sshd[6232]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:33 primorec sshd[6232]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:34 primorec sshd[6234]: Connection from 77.240.189.2 port 43573
Jul  5 11:58:35 primorec sshd[6234]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:35 primorec sshd[6234]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:36 primorec sshd[6236]: Connection from 77.240.189.2 port 43909
Jul  5 11:58:37 primorec sshd[6236]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:37 primorec sshd[6236]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:37 primorec sshd[6238]: Connection from 77.240.189.2 port 44218
Jul  5 11:58:39 primorec sshd[6238]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:39 primorec sshd[6238]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:39 primorec sshd[6240]: Connection from 77.240.189.2 port 44559
Jul  5 11:58:41 primorec sshd[6240]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:41 primorec sshd[6240]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:41 primorec sshd[6242]: Connection from 77.240.189.2 port 44898
Jul  5 11:58:43 primorec sshd[6242]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:43 primorec sshd[6242]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:44 primorec sshd[6244]: Connection from 77.240.189.2 port 45200
Jul  5 11:58:45 primorec sshd[6244]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:45 primorec sshd[6244]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:45 primorec sshd[6246]: Connection from 77.240.189.2 port 45526
Jul  5 11:58:47 primorec sshd[6246]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:47 primorec sshd[6246]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:47 primorec sshd[6248]: Connection from 77.240.189.2 port 45840
Jul  5 11:58:48 primorec sshd[6248]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:48 primorec sshd[6248]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:49 primorec sshd[6250]: Connection from 77.240.189.2 port 46137
Jul  5 11:58:50 primorec sshd[6250]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:50 primorec sshd[6250]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:51 primorec sshd[6252]: Connection from 77.240.189.2 port 46487
Jul  5 11:58:52 primorec sshd[6252]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:52 primorec sshd[6252]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:53 primorec sshd[6254]: Connection from 77.240.189.2 port 46782
Jul  5 11:58:54 primorec sshd[6254]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:54 primorec sshd[6254]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:54 primorec sshd[6256]: Connection from 77.240.189.2 port 47087
Jul  5 11:58:56 primorec sshd[6256]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:56 primorec sshd[6256]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:56 primorec sshd[6258]: Connection from 77.240.189.2 port 47377
Jul  5 11:58:57 primorec sshd[6258]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:57 primorec sshd[6258]: Invalid user testuser from 77.240.189.2
Jul  5 11:58:58 primorec sshd[6260]: Connection from 77.240.189.2 port 47702
Jul  5 11:58:59 primorec sshd[6260]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:58:59 primorec sshd[6260]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:00 primorec sshd[6262]: Connection from 77.240.189.2 port 48017
Jul  5 11:59:01 primorec sshd[6262]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:01 primorec sshd[6262]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:01 primorec sshd[6264]: Connection from 77.240.189.2 port 48319
Jul  5 11:59:02 primorec sshd[6264]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:02 primorec sshd[6264]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:03 primorec sshd[6266]: Connection from 77.240.189.2 port 48619
Jul  5 11:59:04 primorec sshd[6266]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:04 primorec sshd[6266]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:05 primorec sshd[6268]: Connection from 77.240.189.2 port 48945
Jul  5 11:59:06 primorec sshd[6268]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:06 primorec sshd[6268]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:06 primorec sshd[6270]: Connection from 77.240.189.2 port 49246
Jul  5 11:59:08 primorec sshd[6270]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:08 primorec sshd[6270]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:08 primorec sshd[6272]: Connection from 77.240.189.2 port 49542
Jul  5 11:59:10 primorec sshd[6272]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:10 primorec sshd[6272]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:10 primorec sshd[6274]: Connection from 77.240.189.2 port 49899
Jul  5 11:59:12 primorec sshd[6274]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:12 primorec sshd[6274]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:12 primorec sshd[6276]: Connection from 77.240.189.2 port 50203
Jul  5 11:59:14 primorec sshd[6276]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:14 primorec sshd[6276]: Invalid user testuser from 77.240.189.2
Jul  5 11:59:14 primorec sshd[6278]: Connection from 77.240.189.2 port 50540
Jul  5 11:59:16 primorec sshd[6278]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:16 primorec sshd[6278]: Invalid user testy from 77.240.189.2
Jul  5 11:59:16 primorec sshd[6280]: Connection from 77.240.189.2 port 50831
Jul  5 11:59:18 primorec sshd[6280]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:18 primorec sshd[6280]: Invalid user user from 77.240.189.2
Jul  5 11:59:18 primorec sshd[6282]: Connection from 77.240.189.2 port 51167
Jul  5 11:59:19 primorec sshd[6282]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:19 primorec sshd[6282]: Invalid user user from 77.240.189.2
Jul  5 11:59:20 primorec sshd[6284]: Connection from 77.240.189.2 port 51452
Jul  5 11:59:21 primorec sshd[6284]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:21 primorec sshd[6284]: Invalid user user from 77.240.189.2
Jul  5 11:59:21 primorec sshd[6286]: Connection from 77.240.189.2 port 51733
Jul  5 11:59:23 primorec sshd[6286]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:23 primorec sshd[6286]: Invalid user user from 77.240.189.2
Jul  5 11:59:23 primorec sshd[6288]: Connection from 77.240.189.2 port 52057
Jul  5 11:59:25 primorec sshd[6288]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:25 primorec sshd[6288]: Invalid user user from 77.240.189.2
Jul  5 11:59:25 primorec sshd[6290]: Connection from 77.240.189.2 port 52345
Jul  5 11:59:26 primorec sshd[6290]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:26 primorec sshd[6290]: Invalid user user from 77.240.189.2
Jul  5 11:59:27 primorec sshd[6292]: Connection from 77.240.189.2 port 52692
Jul  5 11:59:28 primorec sshd[6292]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:28 primorec sshd[6292]: Invalid user user from 77.240.189.2
Jul  5 11:59:28 primorec sshd[6294]: Connection from 77.240.189.2 port 52953
Jul  5 11:59:30 primorec sshd[6294]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:30 primorec sshd[6294]: Invalid user user from 77.240.189.2
Jul  5 11:59:30 primorec sshd[6296]: Connection from 77.240.189.2 port 53260
Jul  5 11:59:32 primorec sshd[6296]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:32 primorec sshd[6296]: Invalid user user from 77.240.189.2
Jul  5 11:59:32 primorec sshd[6298]: Connection from 77.240.189.2 port 53571
Jul  5 11:59:34 primorec sshd[6298]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:34 primorec sshd[6298]: Invalid user user from 77.240.189.2
Jul  5 11:59:34 primorec sshd[6300]: Connection from 77.240.189.2 port 53845
Jul  5 11:59:36 primorec sshd[6300]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:36 primorec sshd[6300]: Invalid user user from 77.240.189.2
Jul  5 11:59:36 primorec sshd[6343]: Connection from 77.240.189.2 port 54203
Jul  5 11:59:37 primorec sshd[6343]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:37 primorec sshd[6343]: Invalid user user from 77.240.189.2
Jul  5 11:59:38 primorec sshd[6353]: Connection from 77.240.189.2 port 54464
Jul  5 11:59:39 primorec sshd[6353]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:39 primorec sshd[6353]: Invalid user user from 77.240.189.2
Jul  5 11:59:39 primorec sshd[6355]: Connection from 77.240.189.2 port 54758
Jul  5 11:59:41 primorec sshd[6355]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:41 primorec sshd[6355]: Invalid user user from 77.240.189.2
Jul  5 11:59:41 primorec sshd[6357]: Connection from 77.240.189.2 port 55096
Jul  5 11:59:43 primorec sshd[6357]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:43 primorec sshd[6357]: Invalid user user from 77.240.189.2
Jul  5 11:59:43 primorec sshd[6359]: Connection from 77.240.189.2 port 55351
Jul  5 11:59:44 primorec sshd[6359]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:44 primorec sshd[6359]: Invalid user user from 77.240.189.2
Jul  5 11:59:45 primorec sshd[6361]: Connection from 77.240.189.2 port 55692
Jul  5 11:59:46 primorec sshd[6361]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:46 primorec sshd[6361]: Invalid user user from 77.240.189.2
Jul  5 11:59:47 primorec sshd[6373]: Connection from 77.240.189.2 port 56007
Jul  5 11:59:48 primorec sshd[6373]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:48 primorec sshd[6373]: Invalid user user from 77.240.189.2
Jul  5 11:59:49 primorec sshd[6377]: Connection from 77.240.189.2 port 56310
Jul  5 11:59:50 primorec sshd[6377]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:50 primorec sshd[6377]: Invalid user user from 77.240.189.2
Jul  5 11:59:50 primorec sshd[6379]: Connection from 77.240.189.2 port 56568
Jul  5 11:59:52 primorec sshd[6379]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:52 primorec sshd[6379]: Invalid user user from 77.240.189.2
Jul  5 11:59:52 primorec sshd[6381]: Connection from 77.240.189.2 port 56905
Jul  5 11:59:53 primorec sshd[6381]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:53 primorec sshd[6381]: Invalid user user from 77.240.189.2
Jul  5 11:59:54 primorec sshd[6383]: Connection from 77.240.189.2 port 57173
Jul  5 11:59:55 primorec sshd[6383]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:55 primorec sshd[6383]: Invalid user user from 77.240.189.2
Jul  5 11:59:55 primorec sshd[6385]: Connection from 77.240.189.2 port 35297
Jul  5 11:59:57 primorec sshd[6385]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:57 primorec sshd[6385]: Invalid user user1 from 77.240.189.2
Jul  5 11:59:57 primorec sshd[6387]: Connection from 77.240.189.2 port 35587
Jul  5 11:59:58 primorec sshd[6387]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 11:59:58 primorec sshd[6387]: Invalid user user1 from 77.240.189.2
Jul  5 11:59:59 primorec sshd[6389]: Connection from 77.240.189.2 port 35877
Jul  5 12:00:00 primorec sshd[6389]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:00 primorec sshd[6389]: Invalid user user2 from 77.240.189.2
Jul  5 12:00:01 primorec sshd[6406]: Connection from 77.240.189.2 port 36201
Jul  5 12:00:02 primorec sshd[6406]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:02 primorec sshd[6406]: Invalid user user2 from 77.240.189.2
Jul  5 12:00:02 primorec sshd[6563]: Connection from 77.240.189.2 port 36468
Jul  5 12:00:04 primorec sshd[6563]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:04 primorec sshd[6563]: Invalid user user3 from 77.240.189.2
Jul  5 12:00:04 primorec sshd[6878]: Connection from 77.240.189.2 port 36783
Jul  5 12:00:05 primorec sshd[6878]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:05 primorec sshd[6878]: Invalid user user4 from 77.240.189.2
Jul  5 12:00:06 primorec sshd[6880]: Connection from 77.240.189.2 port 37070
Jul  5 12:00:07 primorec sshd[6880]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:07 primorec sshd[6880]: Invalid user user5 from 77.240.189.2
Jul  5 12:00:07 primorec sshd[6882]: Connection from 77.240.189.2 port 37347
Jul  5 12:00:08 primorec sshd[6882]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:08 primorec sshd[6882]: Invalid user user6 from 77.240.189.2
Jul  5 12:00:09 primorec sshd[6884]: Connection from 77.240.189.2 port 37628
Jul  5 12:00:10 primorec sshd[6884]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:10 primorec sshd[6884]: Invalid user user7 from 77.240.189.2
Jul  5 12:00:11 primorec sshd[6886]: Connection from 77.240.189.2 port 37951
Jul  5 12:00:12 primorec sshd[6886]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:12 primorec sshd[6886]: Invalid user user8 from 77.240.189.2
Jul  5 12:00:12 primorec sshd[6898]: Connection from 77.240.189.2 port 38211
Jul  5 12:00:13 primorec sshd[6898]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:13 primorec sshd[6898]: Invalid user user9 from 77.240.189.2
Jul  5 12:00:14 primorec sshd[6902]: Connection from 77.240.189.2 port 38494
Jul  5 12:00:16 primorec sshd[6902]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:16 primorec sshd[6902]: Invalid user username from 77.240.189.2
Jul  5 12:00:16 primorec sshd[6904]: Connection from 77.240.189.2 port 38816
Jul  5 12:00:17 primorec sshd[6904]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:17 primorec sshd[6904]: Invalid user username from 77.240.189.2
Jul  5 12:00:18 primorec sshd[6906]: Connection from 77.240.189.2 port 39089
Jul  5 12:00:19 primorec sshd[6906]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:19 primorec sshd[6906]: Invalid user users from 77.240.189.2
Jul  5 12:00:19 primorec sshd[6908]: Connection from 77.240.189.2 port 39397
Jul  5 12:00:21 primorec sshd[6908]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:21 primorec sshd[6908]: Invalid user wbe from 77.240.189.2
Jul  5 12:00:21 primorec sshd[6910]: Connection from 77.240.189.2 port 39659
Jul  5 12:00:22 primorec sshd[6910]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:22 primorec sshd[6910]: Invalid user wbe from 77.240.189.2
Jul  5 12:00:23 primorec sshd[6912]: Connection from 77.240.189.2 port 39934
Jul  5 12:00:24 primorec sshd[6912]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:24 primorec sshd[6912]: Invalid user web from 77.240.189.2
Jul  5 12:00:25 primorec sshd[6914]: Connection from 77.240.189.2 port 40263
Jul  5 12:00:26 primorec sshd[6914]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:26 primorec sshd[6914]: Invalid user web from 77.240.189.2
Jul  5 12:00:26 primorec sshd[6917]: Connection from 77.240.189.2 port 40526
Jul  5 12:00:28 primorec sshd[6917]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:28 primorec sshd[6917]: Invalid user web from 77.240.189.2
Jul  5 12:00:28 primorec sshd[6919]: Connection from 77.240.189.2 port 40844
Jul  5 12:00:30 primorec sshd[6919]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:30 primorec sshd[6919]: Invalid user web from 77.240.189.2
Jul  5 12:00:30 primorec sshd[6921]: Connection from 77.240.189.2 port 41126
Jul  5 12:00:31 primorec sshd[6921]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:31 primorec sshd[6921]: Invalid user web from 77.240.189.2
Jul  5 12:00:32 primorec sshd[6923]: Connection from 77.240.189.2 port 41383
Jul  5 12:00:33 primorec sshd[6923]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:33 primorec sshd[6923]: Invalid user web from 77.240.189.2
Jul  5 12:00:34 primorec sshd[6925]: Connection from 77.240.189.2 port 41713
Jul  5 12:00:35 primorec sshd[6925]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:35 primorec sshd[6925]: Invalid user web from 77.240.189.2
Jul  5 12:00:35 primorec sshd[6927]: Connection from 77.240.189.2 port 41985
Jul  5 12:00:37 primorec sshd[6927]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:37 primorec sshd[6927]: Invalid user web from 77.240.189.2
Jul  5 12:00:37 primorec sshd[6929]: Connection from 77.240.189.2 port 42299
Jul  5 12:00:39 primorec sshd[6929]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:39 primorec sshd[6929]: Invalid user web from 77.240.189.2
Jul  5 12:00:39 primorec sshd[6931]: Connection from 77.240.189.2 port 42561
Jul  5 12:00:40 primorec sshd[6931]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:40 primorec sshd[6931]: Invalid user web from 77.240.189.2
Jul  5 12:00:40 primorec sshd[6933]: Connection from 77.240.189.2 port 42827
Jul  5 12:00:42 primorec sshd[6933]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:42 primorec sshd[6933]: Invalid user web from 77.240.189.2
Jul  5 12:00:42 primorec sshd[6935]: Connection from 77.240.189.2 port 43144
Jul  5 12:00:43 primorec sshd[6935]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:43 primorec sshd[6935]: Invalid user web from 77.240.189.2
Jul  5 12:00:44 primorec sshd[6937]: Connection from 77.240.189.2 port 43389
Jul  5 12:00:45 primorec sshd[6937]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:45 primorec sshd[6937]: Invalid user web from 77.240.189.2
Jul  5 12:00:45 primorec sshd[6939]: Connection from 77.240.189.2 port 43663
Jul  5 12:00:47 primorec sshd[6939]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:47 primorec sshd[6939]: Invalid user web from 77.240.189.2
Jul  5 12:00:47 primorec sshd[6941]: Connection from 77.240.189.2 port 43971
Jul  5 12:00:48 primorec sshd[6941]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:48 primorec sshd[6941]: Invalid user web from 77.240.189.2
Jul  5 12:00:49 primorec sshd[6943]: Connection from 77.240.189.2 port 44247
Jul  5 12:00:50 primorec sshd[6943]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:50 primorec sshd[6943]: Invalid user web from 77.240.189.2
Jul  5 12:00:50 primorec sshd[6945]: Connection from 77.240.189.2 port 44496
Jul  5 12:00:51 primorec sshd[6945]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:51 primorec sshd[6945]: Invalid user web from 77.240.189.2
Jul  5 12:00:52 primorec sshd[6952]: Connection from 77.240.189.2 port 44755
Jul  5 12:00:53 primorec sshd[6952]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:53 primorec sshd[6952]: Invalid user web from 77.240.189.2
Jul  5 12:00:53 primorec sshd[6959]: Connection from 77.240.189.2 port 45048
Jul  5 12:00:55 primorec sshd[6959]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:55 primorec sshd[6959]: Invalid user web from 77.240.189.2
Jul  5 12:00:55 primorec sshd[6962]: Connection from 77.240.189.2 port 45319
Jul  5 12:00:56 primorec sshd[6962]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:56 primorec sshd[6962]: Invalid user web from 77.240.189.2
Jul  5 12:00:56 primorec sshd[6964]: Connection from 77.240.189.2 port 45527
Jul  5 12:00:57 primorec sshd[6964]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:57 primorec sshd[6964]: Invalid user web from 77.240.189.2
Jul  5 12:00:58 primorec sshd[6966]: Connection from 77.240.189.2 port 45826
Jul  5 12:00:59 primorec sshd[6966]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:00:59 primorec sshd[6966]: Invalid user web from 77.240.189.2
Jul  5 12:01:00 primorec sshd[6968]: Connection from 77.240.189.2 port 46100
Jul  5 12:01:01 primorec sshd[6968]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:01 primorec sshd[6968]: Invalid user web from 77.240.189.2
Jul  5 12:01:01 primorec sshd[6970]: Connection from 77.240.189.2 port 46371
Jul  5 12:01:02 primorec sshd[6970]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:02 primorec sshd[6970]: Invalid user web from 77.240.189.2
Jul  5 12:01:02 primorec sshd[6972]: Connection from 77.240.189.2 port 46609
Jul  5 12:01:03 primorec sshd[6972]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:03 primorec sshd[6972]: Invalid user web from 77.240.189.2
Jul  5 12:01:04 primorec sshd[6974]: Connection from 77.240.189.2 port 46856
Jul  5 12:01:05 primorec sshd[6974]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:05 primorec sshd[6974]: Invalid user web from 77.240.189.2
Jul  5 12:01:05 primorec sshd[6976]: Connection from 77.240.189.2 port 47141
Jul  5 12:01:06 primorec sshd[6976]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:06 primorec sshd[6976]: Invalid user web from 77.240.189.2
Jul  5 12:01:06 primorec sshd[6978]: Connection from 77.240.189.2 port 47352
Jul  5 12:01:07 primorec sshd[6978]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:07 primorec sshd[6978]: Invalid user web from 77.240.189.2
Jul  5 12:01:08 primorec sshd[6980]: Connection from 77.240.189.2 port 47576
Jul  5 12:01:09 primorec sshd[6980]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:09 primorec sshd[6980]: Invalid user web from 77.240.189.2
Jul  5 12:01:09 primorec sshd[6982]: Connection from 77.240.189.2 port 47884
Jul  5 12:01:11 primorec sshd[6982]: reverse mapping checking getaddrinfo for 2-189-240-77-persefone.mpcom.cz [77.240.189.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul  5 12:01:11 primorec sshd[6982]: Invalid user web from 77.240.189.2
```

I use pub key for authentication not password but i use standard port 22 for ssh.

I really won't worry about it. Don't use conventional usernames, and as you said your not even logging in though a user account. Read though the ssh config files and the pam config files. The comments will teach you more then you will learn here.

Most attackers will try 100 or attempts on the root account. Just disable the root account.

---

### Post by triangleSLO on 2009-07-18
> **triangleSLO said:**
> Can you tell me if he got access to my computer?
I checked ip and its quite famous. I dont see any access denied messages or anything :/

```
Jul 12 20:42:09 primorec sshd[22674]: Connection from 61.129.60.23 port 60911
Jul 12 20:42:17 primorec sshd[22676]: Connection from 61.129.60.23 port 33248
Jul 12 20:42:25 primorec sshd[22678]: Connection from 61.129.60.23 port 33823
Jul 12 20:42:32 primorec sshd[22680]: Connection from 61.129.60.23 port 34409
Jul 12 20:42:40 primorec sshd[22682]: Connection from 61.129.60.23 port 34955
Jul 12 20:42:48 primorec sshd[22684]: Connection from 61.129.60.23 port 35490
Jul 12 20:42:56 primorec sshd[22686]: Connection from 61.129.60.23 port 36037
Jul 12 20:43:04 primorec sshd[22688]: Connection from 61.129.60.23 port 36569
Jul 12 20:43:12 primorec sshd[22690]: Connection from 61.129.60.23 port 37101
Jul 12 20:43:19 primorec sshd[22692]: Connection from 61.129.60.23 port 37665
Jul 12 20:43:27 primorec sshd[22694]: Connection from 61.129.60.23 port 38175
Jul 12 20:43:35 primorec sshd[22696]: Connection from 61.129.60.23 port 38713
Jul 12 20:43:43 primorec sshd[22698]: Connection from 61.129.60.23 port 39257
Jul 12 20:43:51 primorec sshd[22700]: Connection from 61.129.60.23 port 39803
Jul 12 20:43:59 primorec sshd[22702]: Connection from 61.129.60.23 port 40327
Jul 12 20:44:06 primorec sshd[22704]: Connection from 61.129.60.23 port 40884
Jul 12 20:44:14 primorec sshd[22706]: Connection from 61.129.60.23 port 41417
Jul 12 20:44:22 primorec sshd[22708]: Connection from 61.129.60.23 port 41969
Jul 12 20:44:30 primorec sshd[22710]: Connection from 61.129.60.23 port 60195
Jul 12 20:44:38 primorec sshd[22712]: Connection from 61.129.60.23 port 60755
Jul 12 20:44:46 primorec sshd[22714]: Connection from 61.129.60.23 port 33085
Jul 12 20:44:53 primorec sshd[22716]: Connection from 61.129.60.23 port 33641
Jul 12 20:45:01 primorec sshd[22718]: Connection from 61.129.60.23 port 34193
Jul 12 20:45:09 primorec sshd[22720]: Connection from 61.129.60.23 port 34720
Jul 12 20:45:17 primorec sshd[22722]: Connection from 61.129.60.23 port 35279
Jul 12 20:45:25 primorec sshd[22724]: Connection from 61.129.60.23 port 35800
Jul 12 20:45:32 primorec sshd[22726]: Connection from 61.129.60.23 port 36340
Jul 12 20:45:40 primorec sshd[22728]: Connection from 61.129.60.23 port 36870
Jul 12 20:45:48 primorec sshd[22730]: Connection from 61.129.60.23 port 37411
Jul 12 20:45:56 primorec sshd[22732]: Connection from 61.129.60.23 port 37965
Jul 12 20:46:04 primorec sshd[22734]: Connection from 61.129.60.23 port 38513
Jul 12 21:38:34 primorec sshd[23793]: Connection from 173.45.72.186 port 43576
Jul 12 21:38:36 primorec sshd[23795]: Connection from 173.45.72.186 port 43726
Jul 12 21:38:37 primorec sshd[23797]: Connection from 173.45.72.186 port 43887

```

So is this a failed connection attempt?

---

### Post by ArchCast on 2009-07-18
I used to get that a lot on my server.  Changing the default ssh port, installing and running fail2ban and disabling root should suffice.  :)

---

### Post by TurboRush on 2009-07-20
Just install DenyHosts and the IP will get blocked after X number of failed attempts.. I see very few return attempts from IP's once they've been blocked.

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

---

### Post by grayn0de on 2009-07-20
I agree. Either add the IP addresses manually to host.deny or use DenyHost for the automagic goodness. Also, reconfigure sshd to listen on a nondefault port. These kind of attacks are usually automated, which means the attacker is not taking the time to do any kind of portscan. Rather, they simply try to brute force port 22. This happens quite frequently, actually.

---

### Post by bodhi.zazen on 2009-07-20
Or iptables ...

deny hosts is nice and fast to install. Once you learn iptables you will understand networking, services, and see iptables is elegant in it's implementation.

---

