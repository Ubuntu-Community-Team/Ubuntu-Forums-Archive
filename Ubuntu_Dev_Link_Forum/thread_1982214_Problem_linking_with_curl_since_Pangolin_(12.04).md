---
title: "Problem linking with curl since Pangolin (12.04)"
date: 2012-05-18
forum: Ubuntu Dev Link Forum
---

### Post by Zakhafr on 2012-05-18
Hello,

I have a problem linking programs using curl since 12.04

For example, even with the example givent with the curl development documentations: cookie_interface.c below

```
/*****************************************************************************
 *                                  _   _ ____  _
 *  Project                     ___| | | |  _ \| |
 *                             / __| | | | |_) | |
 *                            | (__| |_| |  _ <| |___
 *                             \___|\___/|_| \_\_____|
 *
 *  This example shows usage of simple cookie interface. 
 */

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <errno.h>
#include <time.h>

#include <curl/curl.h>

static void
print_cookies(CURL *curl)
{
  CURLcode res;
  struct curl_slist *cookies;
  struct curl_slist *nc;
  int i;

  printf("Cookies, curl knows:\n");
  res = curl_easy_getinfo(curl, CURLINFO_COOKIELIST, &cookies);
  if (res != CURLE_OK) {
    fprintf(stderr, "Curl curl_easy_getinfo failed: %s\n", curl_easy_strerror(res));
    exit(1);
  }
  nc = cookies, i = 1;
  while (nc) {
    printf("[%d]: %s\n", i, nc->data);
    nc = nc->next;
    i++;
  }
  if (i == 1) {
    printf("(none)\n");
  }
  curl_slist_free_all(cookies);
}

int
main(void)
{
  CURL *curl;
  CURLcode res;

  curl_global_init(CURL_GLOBAL_ALL);
  curl = curl_easy_init();
  if (curl) {
    char nline[256];

    curl_easy_setopt(curl, CURLOPT_URL, "http://www.google.com/"); /* google.com sets "PREF" cookie */
    curl_easy_setopt(curl, CURLOPT_VERBOSE, 1L);
    curl_easy_setopt(curl, CURLOPT_COOKIEFILE, ""); /* just to start the cookie engine */
    res = curl_easy_perform(curl);
    if (res != CURLE_OK) {
      fprintf(stderr, "Curl perform failed: %s\n", curl_easy_strerror(res));
      return 1;
    }

    print_cookies(curl);

    printf("Erasing curl's knowledge of cookies!\n");
    curl_easy_setopt(curl, CURLOPT_COOKIELIST, "ALL");

    print_cookies(curl);

    printf("-----------------------------------------------\n"
           "Setting a cookie \"PREF\" via cookie interface:\n");
#ifdef WIN32
#define snprintf _snprintf
#endif
    /* Netscape format cookie */
    snprintf(nline, sizeof(nline), "%s\t%s\t%s\t%s\t%lu\t%s\t%s",
      ".google.com", "TRUE", "/", "FALSE", time(NULL) + 31337, "PREF", "hello google, i like you very much!");
    res = curl_easy_setopt(curl, CURLOPT_COOKIELIST, nline);
    if (res != CURLE_OK) {
      fprintf(stderr, "Curl curl_easy_setopt failed: %s\n", curl_easy_strerror(res));
      return 1;            
    }

    /* HTTP-header style cookie */
    snprintf(nline, sizeof(nline),
      "Set-Cookie: OLD_PREF=3d141414bf4209321; "
      "expires=Sun, 17-Jan-2038 19:14:07 GMT; path=/; domain=.google.com");
    res = curl_easy_setopt(curl, CURLOPT_COOKIELIST, nline);
    if (res != CURLE_OK) {
      fprintf(stderr, "Curl curl_easy_setopt failed: %s\n", curl_easy_strerror(res));
      return 1;            
    }

    print_cookies(curl);

    res = curl_easy_perform(curl);
    if (res != CURLE_OK) {
      fprintf(stderr, "Curl perform failed: %s\n", curl_easy_strerror(res));
      return 1;
    }
  }
  else {
    fprintf(stderr, "Curl init failed!\n");
    return 1;
  }

  curl_global_cleanup();
  return 0;
}
```

Normally, it is compiled/linked with one command line, and it was working on 10.04, this way:
```
`curl-config --cc --cflags --libs`  -o cookie_interface cookie_interface.c
```

Of course, I have installed the libcurl stuff with:
```
sudo apt-get install libcurl4-gnutls-dev
```

And since 12.04, I get:
```
$ `curl-config --cc --cflags --libs`  -o cookie_interface cookie_interface.c 
/tmp/ccyjd6nn.o: In function `print_cookies':
cookie_interface.c:(.text+0xc3): undefined reference to `curl_easy_getinfo'
cookie_interface.c:(.text+0xd6): undefined reference to `curl_easy_strerror'
cookie_interface.c:(.text+0x161): undefined reference to `curl_slist_free_all'
/tmp/ccyjd6nn.o: In function `main':
cookie_interface.c:(.text+0x187): undefined reference to `curl_global_init'
cookie_interface.c:(.text+0x18c): undefined reference to `curl_easy_init'
cookie_interface.c:(.text+0x1cc): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x1f7): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x222): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x231): undefined reference to `curl_easy_perform'
cookie_interface.c:(.text+0x24d): undefined reference to `curl_easy_strerror'
cookie_interface.c:(.text+0x2ba): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x35f): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x37b): undefined reference to `curl_easy_strerror'
cookie_interface.c:(.text+0x3ef): undefined reference to `curl_easy_setopt'
cookie_interface.c:(.text+0x40b): undefined reference to `curl_easy_strerror'
cookie_interface.c:(.text+0x452): undefined reference to `curl_easy_perform'
cookie_interface.c:(.text+0x46e): undefined reference to `curl_easy_strerror'
cookie_interface.c:(.text+0x4c4): undefined reference to `curl_global_cleanup'
collect2: ld a retourné 1 code d'état d'exécution

```

So, we see that the compilation is OK, but the linker (ld) does not find ANY of the symbols belonging to libcurl.

I suspect the error is due to the new multiarch organisation, but could also be other things I done wrong.


Any idea on how to solve that (link programs with curl correctly)?

---

### Post by MadCow108 on 2012-05-19
answered here [https://bugs.launchpad.net/bugs/1001576](https://bugs.launchpad.net/bugs/1001576)
use
```
`curl-config --cc --cflags`  -o cookie_interface cookie_interface.c `curl-config --libs`
```

---

### Post by Zakhafr on 2012-05-19
Yes thank you.

That was me posting the issue on the launchpad. :p

And indeed, it is a documentation issue as the command line in the file curl-config.html is wrong.
So I gave a patch to change it, but as the documentation is generated, I believe upstream has to change it in the source for the fix to be reliable.

=> Marking the thread solved.

---

