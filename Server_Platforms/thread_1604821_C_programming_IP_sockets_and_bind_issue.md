---
title: "C programming: IP sockets and bind issue"
date: 2010-10-24
forum: Server Platforms
---

### Post by jatos on 2010-10-24
Hi

Got this code:


```

#include <stdio.h>          /* stderr, stdout */
#include <sys/socket.h>
#include <arpa/inet.h>
#include <netinet/in.h>
#include <netinet/ip.h> /* superset of previous */
#include <string.h>

int net_listen() {
    int fn_socket, fn_bind_result;
    fn_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (fn_socket < 0) return -1;
    printf ("net_listen: socket created.\n");
    struct sockaddr_in fn_bind_addr;
    memset(&fn_bind_addr, 0, sizeof(struct sockaddr_in));
    fn_bind_addr.sin_family = AF_INET;
    fn_bind_addr.sin_port = htons(4080);
    fn_bind_addr.sin_addr.s_addr = INADDR_ANY;
    fn_bind_result = bind(fn_socket, &fn_bind_addr, sizeof(struct sockaddr_in));
    if (fn_bind_result < 0) return -1;
    printf ("net_listen: bind success");
}

```

> /home/jamie/aws/socket_linux.cpp||In function ‘int net_listen()’:|
/home/jamie/aws/socket_linux.cpp|18|error: cannot convert ‘sockaddr_in*’ to ‘const sockaddr*’ for argument ‘2’ to ‘int bind(int, const sockaddr*, socklen_t)’|
||=== Build finished: 1 errors, 0 warnings ===|

Chucks this up. Any advice?

Jamie

---

### Post by craigp84 on 2010-10-24
```
fn_bind_result = bind(fn_socket, (struct sockaddr *) &fn_bind_addr, sizeof(struct sockaddr_in));
```

:-)

Posted in wrong section though i think?

---

### Post by jatos on 2010-10-24
Tried that, same error.

Which section should it have gone in?

---

### Post by craigp84 on 2010-10-24
You've a problem in your build scripts then - your build infra hasn't noticed you've updated that file - you couldn't get that error with those params. The only way i can imagie right now is you idn't hit save?

I dunno what the other categories are on this site, i only visit server platforms. It's all SysAdmin type Q&A rather than programming.

---

