---
title: "core_output_filter: flushing because of THRESHOLD_MAX_BUFFER"
date: 2018-01-24
forum: Server Platforms
---

### Post by paulomateus on 2018-01-24
Hi,

I've set a new server, with apache2 + SSL + php5.6. On this server i authorize and ecnrypt some files to be uploaded by other devices on the network. But i'm getting some strange behaviour, the upload is not finish with sucess. I've tried everthing and i don't know what to more.
I get this trace4 log on error_log file.
what could cause this error: core_output_filter: flushing because of THRESHOLD_MAX_BUFFER



Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

```
Wed Jan 24 18:54:21.326133 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Content-Disposition: attachment; filename='48f83431a3cb504a5271d083b1b54dff-file.bin.enc'
[Wed Jan 24 18:54:21.326154 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Content-Transfer-Encoding: binary
[Wed Jan 24 18:54:21.326174 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Cache-Control: no-cache,must-revalidate
[Wed Jan 24 18:54:21.326195 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Pragma: no-cache
[Wed Jan 24 18:54:21.326215 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Last-Modified: Wed, 24 Jan 2018 17:54:21 GMT
[Wed Jan 24 18:54:21.326236 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Content-Length: 126923408
[Wed Jan 24 18:54:21.326256 2018] [http:trace4] [pid 5483] http_filters.c(958): [client ipaddr port]   Content-Type: application/octet-stream
[Wed Jan 24 18:54:21.326281 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(1516): [client ipaddr port] coalesce: have 0 bytes, adding 2039 more
[Wed Jan 24 18:54:21.326350 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 2069/2069 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.329616 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.343726 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.353217 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.359447 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.372586 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.377506 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.391819 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.396928 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.401792 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.406648 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.411523 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.416358 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.421189 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.426090 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.430958 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.435795 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.440657 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.445569 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.450494 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.455339 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.460178 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.465023 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.469879 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.474732 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.479558 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.484391 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.489232 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.494111 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)


[Wed Jan 24 18:54:21.498924 2018] [core:trace6] [pid 5483] core_filters.c(525): [client ipaddr port] core_output_filter: flushing because of THRESHOLD_MAX_BUFFER


[Wed Jan 24 18:54:21.591579 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.596474 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.601320 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.606140 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.611000 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.615862 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.620711 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.625588 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.630452 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.635321 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.640188 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.645040 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.650646 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.655508 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.660351 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.665216 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.670067 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.674919 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.679925 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.688797 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.693673 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.698497 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.703351 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.708187 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.713027 2018] [ssl:trace4] [pid 5483] ssl_engine_io.c(2057): [client ipaddr port] OpenSSL: write 8229/8229 bytes to BIO#563ed7c79810 [mem: 563ed7cc8193] (BIO dump follows)
[Wed Jan 24 18:54:21.717882 2018] [core:trace6] [pid 5483] core_filters.c(525): [client ipaddr port] core_output_filter: flushing because of THRESHOLD_MAX_BUFFER
```

---

