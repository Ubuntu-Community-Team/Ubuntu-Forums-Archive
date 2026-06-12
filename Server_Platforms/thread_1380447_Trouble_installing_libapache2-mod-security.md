---
title: "Trouble installing libapache2-mod-security"
date: 2010-01-13
forum: Server Platforms
---

### Post by sp0nge on 2010-01-13
Hello, I am working on building a personal server as securely as possible using Ubuntu 8.04 and Apache 2.2.8. I have been reading [this link]("http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security") as my guide to installing mod-security, but continue to find it is not available in my repository on the 8.04 virtual machine (although it is available on my 9.04 host machine). Since I was unsuccessful with the install using apt, I decided to try to build from source using [this link]("http://www.webhostingtalk.com/archive/index.php/t-870523.html") to guide me and got much further but again I have hit a roadblock that I can not fix:

Input:
```
apxs2 -cia mod_security.c
```

Output (this is the tail end of the output where the errors seem to be listed:
```

\msc_xml.h:25:31: error: libxml/xmkschemas.h: No such file or directory
msc_xml.h:26:26: error: libxml/xpath.h: No such file or directory
In file included from modsecurity.h:40,
		 from modsecurity.c:23:
msc_xml.h:31: error: exprectd specifier-qualifier-list before 'xmlSAXHandler'
apsx:Error: Command failed wih rc-65536
```

Can anyone tell me what I'm missing? It seems that it should be trivial to install this module, yet I am constantly hitting dead ends :confused:

---

### Post by sp0nge on 2010-01-14
bump.

can anyone help me here?

---

### Post by Ilalmi on 2010-01-17
Do you have libxml2 and libpcre3 installed?

---

### Post by joshuakimba on 2010-01-21
Bump

I have these errors when using the make install command. My OS is Linux Ubuntu. Do you have any suggestions please?

joshua@joshua-laptop:~/Apache$ **make install**
Making install in srclib
make[1]: Entering directory `/home/joshua/Apache/srclib'
Making install in apr
make[2]: Entering directory `/home/joshua/Apache/srclib/apr'
make[3]: Entering directory `/home/joshua/Apache/srclib/apr'
make[3]: Nothing to be done for `local-all'.
make[3]: Leaving directory `/home/joshua/Apache/srclib/apr'
/home/joshua/Apache/srclib/apr/build/mkdir.sh /usr/local/apache2/lib /usr/local/apache2/bin /usr/local/apache2/build \
           /usr/local/apache2/lib/pkgconfig /usr/local/apache2/include
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/lib
mkdir: cannot create directory `/usr/local/apache2/lib': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/bin
mkdir: cannot create directory `/usr/local/apache2/bin': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/build
mkdir: cannot create directory `/usr/local/apache2/build': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/lib
mkdir: cannot create directory `/usr/local/apache2/lib': No such file or directory
mkdir /usr/local/apache2/lib/pkgconfig
mkdir: cannot create directory `/usr/local/apache2/lib/pkgconfig': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/include
mkdir: cannot create directory `/usr/local/apache2/include': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/joshua/Apache/srclib/apr'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/joshua/Apache/srclib'
make: *** [install-recursive] Error 1
joshua@joshua-laptop:~/Apache$

---

### Post by gombadi on 2010-01-21
> 
joshua@joshua-laptop:~/Apache$ make install
Making install in srclib
make[1]: Entering directory `/home/joshua/Apache/srclib'
Making install in apr
make[2]: Entering directory `/home/joshua/Apache/srclib/apr'
make[3]: Entering directory `/home/joshua/Apache/srclib/apr'
make[3]: Nothing to be done for `local-all'.
make[3]: Leaving directory `/home/joshua/Apache/srclib/apr'
/home/joshua/Apache/srclib/apr/build/mkdir.sh /usr/local/apache2/lib /usr/local/apache2/bin /usr/local/apache2/build \
/usr/local/apache2/lib/pkgconfig /usr/local/apache2/include
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied


make install generally needs to be run as root as it installs files in directories that are owned by root.

Either change to root or add sudo to the make install command.

---

