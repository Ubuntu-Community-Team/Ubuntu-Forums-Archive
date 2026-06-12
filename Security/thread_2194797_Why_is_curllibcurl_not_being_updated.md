---
title: "Why is curl/libcurl not being updated?"
date: 2013-12-20
forum: Security
---

### Post by libcurlisnotbeingu on 2013-12-20
I've been starting to use libcurl to write some simple programs when I realized that the libcurl version that is integrated into Ubuntu 12.04 is way outdated, and contains several known vulnerabilities. The lastest version that is out (libcurl/7.34.0) does not have any known vulnerabilities yet.
```

$ cat test.cpp 
#include <iostream>
#include <curl/curl.h>

int main(int argc, char *argv[]){
    std::cout << curl_version() << std::endl;
    return 0;
}
$ g++ -o test test.cpp -lcurl
$ ./test | grep -o 'libcurl/\([^ ]\+\) '
libcurl/7.22.0 
$ lsb_release -r
Release:    12.04

```

---

### Post by deadflowr on 2013-12-20
It gets patched, regularly
[http://changelogs.ubuntu.com/changelogs/pool/main/c/curl/curl_7.22.0-3ubuntu4.6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/curl/curl_7.22.0-3ubuntu4.6/changelog)

---

### Post by kostkon on 2013-12-20
All ubuntu packages are patched against any known vulnerabilities, list is [here]("http://www.ubuntu.com/usn/").

---

