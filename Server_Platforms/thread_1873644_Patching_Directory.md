---
title: "Patching Directory"
date: 2011-11-01
forum: Server Platforms
---

### Post by person287 on 2011-11-01
Hi,

I'm trying to patch something (Adito to run behind Reverse Proxy), but I'm not sure what I'm doing wrong. I cd into the directory when the files and patch file are but when I put in 

```
sudo patch openvpn-als-reverse-proxy.patch
```

it just hangs forever. Does anybody have any suggestions or am I just doing it totally wrong?

Thanks, Ed

---

### Post by Wej on 2011-11-01
Not sure if this will help, but are you trying to patch the binary files, or the source code? From what I can tell in the patch man pages, you need to patch the source code and re-compile it. It doesn't patch binary files. I found that openvpn-als-reverse-proxy.patch file on sourceforge and it appears to be an ascii file, which leads me further to believe that it needs to be patching the source code for the application.

Are you trying to patch the source code?

---

### Post by person287 on 2011-11-01
As far as I know java compiles it on the fly. I downloaded a .tar.gz file that seemed to be in "java text" and all I did was unzip it. I might be wrong but that's what I thought.

---

