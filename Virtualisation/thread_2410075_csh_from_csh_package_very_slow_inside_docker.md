---
title: "csh from csh package very slow inside docker"
date: 2019-01-10
forum: Virtualisation
---

### Post by clarkera1971 on 2019-01-10
I have a work around for this issue, but am reporting it as I could not find any solutions documented on-line.
Working with docker containers, I noticed that if I install the csh package then it is very slow to start on our HPC system.
This became noticeable when running lots of small scripts and the performance dropped dramatically.
After a lot testing, I tried using the tcsh package instead which provides an alternative version of csh and it's start up was much better.
The key thing is to NOT install the csh package and only install the tcsh alternative.

To see the issue, I created 3 scripts for running the ls command:

```

#!/bin/bash -f
ls

```

```

#!/bin/csh -f
ls

```

```

#!/bin/tcsh -f
ls

```

My minimal docker file is:
```

from ubuntu:18.04

RUN DEBIAN_FRONTEND=noninteractive apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -q -y csh tcsh

COPY ls.tcsh /.
COPY ls.csh /.
COPY ls.sh /.

```

I now compare the times inside and outside of the containers:
```

docker build -t test_csh -f ./csh.docker .

time ./ls.sh
time ./ls.csh
time ./ls.tcsh
docker run -it --rm test_csh /bin/bash -c "time ./ls.sh"
docker run -it --rm test_csh /bin/bash -c "time ./ls.csh"
docker run -it --rm test_csh /bin/bash -c "time ./ls.tcsh"

```

build_test_csh  csh.docker  ls.csh  ls.sh  ls.tcsh                                                                               

real    0m0.004s **<-- bash without docker**
user    0m0.000s
sys     0m0.004s
build_test_csh  csh.docker  ls.csh  ls.sh  ls.tcsh

real    0m0.007s**<-- csh without docker**
user    0m0.004s
sys     0m0.003s
build_test_csh  csh.docker  ls.csh  ls.sh  ls.tcsh

real    0m0.007s**<-- tcsh without docker**
user    0m0.001s
sys     0m0.006s
bin   dev  home  lib64   ls.sh    media  opt   root  sbin  sys  usr
boot  etc  lib   ls.csh  ls.tcsh  mnt    proc  run   srv   tmp  var

real    0m0.003s**<-- bash inside docker**
user    0m0.001s
sys     0m0.003s
bin  boot  dev  etc  home  lib  lib64  ls.csh  ls.sh  ls.tcsh  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

real    0m4.651s**<-- csh inside docker, notice that it is taking ~x1000 longer**
user    0m0.362s
sys     0m4.272s
bin   dev  home  lib64   ls.sh    media  opt   root  sbin  sys  usr
boot  etc  lib   ls.csh  ls.tcsh  mnt    proc  run   srv   tmp  var

real    0m0.015s**<-- tcsh inside docker**
user    0m0.001s
sys     0m0.003s


If I change the docker file to only install the tcsh package, then it provides a different csh and then the new time for csh drops down to:

real    0m0.004s **<-- csh inside docker when using csh from the tcsh package**
user    0m0.000s
sys     0m0.004s

---

