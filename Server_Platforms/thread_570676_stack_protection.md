---
title: "stack protection"
date: 2007-10-08
forum: Server Platforms
---

### Post by Dillius on 2007-10-08
I'm taking a class where I have a homework assignment to write a buffer overflow. The professor pointed us to "Smashing the stack for fun and profit" but I still need to find a way to disable stack protection so that I can actually do it. (Or find an old linux that doesn't have stack protection to install)

I currently use Ubuntu 7.04 and of course have root privileges to work with. I'm willing to use any distro, I'm just more familiar and already have a running installation of Ubuntu, so I would prefer to just be able to turn off (and hopefully later back on) the stack protection for this assignment without having to install an entire OS just to do this one thing.

So far asking for help on this matter has only led to me having threads on other forums locked, but maybe the Ubuntu community can save me on this one. Any help is greatly appreciated.

---

### Post by Dillius on 2007-10-09
I found a previous discussion where someone mentioned:

```
sudo bash -c 'echo "kernel.randomize_va_space = 0" >> /etc/sysctl.conf'
sudo /sbin/sysctl -p
```

Will try it out, but have still found no thorough discussions on the topic.

---

### Post by Dillius on 2007-10-11
Bump. Still nothing.

---

### Post by Adnarim on 2007-10-12
There are two different protection shemes you have to bypass in Ubuntu to trigger a buffer overflow.

1.) Non-executable stack forced by compiling with gcc
2.) Virtual Adressspace Randomisation forced by the kernel

Well because you make it for the school I think you wanna go the easy whay and simply switch these protections off:

1.) You have to compile your proof of concept application with the -fno-stack-protector switch:
```

bash:~/Desktop$ cat test.c
#include <stdio.h>

int main (void) {
     char buff[10];
     scanf("%s",buff); 

     return 0;
}
bash:~/Desktop$ gcc -o buff test.c
bash:~/Desktop$ ./buff 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
*** stack smashing detected ***: ./buff terminated
Aborted
bash:~/Desktop$ gcc -fno-stack-protector -o buff test.c
bash:~/Desktop$ ./buff 
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA 
Segmentation fault
bash:~/Desktop$ 

```
2.) To switch the virtual-adress-space-randomisation of you have to be root. So type **sudo su**. After that you can switch it off with: **echo 0 > /proc/sys/kernel/randomize_va_space** and on again with echo 1 > ...

---

