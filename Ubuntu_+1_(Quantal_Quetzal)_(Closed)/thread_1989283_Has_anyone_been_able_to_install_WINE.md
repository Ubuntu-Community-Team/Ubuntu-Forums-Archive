---
title: "Has anyone been able to install WINE?"
date: 2012-05-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cheesemill on 2012-05-28
Hi there guys.

I've been trying to install WINE on my Quantal machine for several weeks but aptitude has never been able to resolve the dependencies quoting several internal errors. Does anyone know if this is a problem with aptitude or just a case of the required packages not being in sync on the repositories?

Also has anyone managed to install WINE (maybe on a 32-bit system) ?

```
root@quantal:~# aptitude install wine
The following NEW packages will be installed:
  binfmt-support{a} fonts-droid{a} fonts-horai-umefont fonts-unfonts-core{a} gcc-4.7-base:i386{a} gettext:i386{ab} gettext-base:i386{ab} gnome-exe-thumbnailer{a} 
  icoutils{a} imagemagick{a} imagemagick-common{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} 
  libavahi-common3:i386{a} libc6:i386{a} libcapi20-3{a} libcapi20-3:i386{a} libcdt4{a} libcomerr2:i386{a} libcroco3:i386{a} libcups2:i386{a} libdb5.1:i386{a} 
  libdbus-1-3:i386{a} libdrm-intel1:i386{a} libdrm-nouveau1a:i386{a} libdrm-radeon1:i386{a} libdrm2:i386{a} libexif12:i386{a} libexpat1:i386{a} libffi6:i386{a} 
  libfontconfig1:i386{a} libfreetype6:i386{a} libgcc1:i386{a} libgcrypt11:i386{a} libgd2-xpm:i386{a} libgettextpo0:i386{a} libgif4:i386{a} libgl1-mesa-dri:i386{a} 
  libgl1-mesa-glx:i386{a} libglapi-mesa:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgnutls26:i386{a} libgomp1:i386{a} libgpg-error0:i386{a} 
  libgphoto2-2:i386{a} libgphoto2-port0:i386{a} libgpm2:i386{a} libgraph4{a} libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} 
  libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libgvc5{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} 
  libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} libice6:i386{a} libieee1284-3:i386{a} libilmbase6{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} liblcms1:i386{a} libldap-2.4-2:i386{a} 
  libllvm3.0:i386{a} liblqr-1-0{a} libltdl7:i386{a} libmagickcore4{a} libmagickcore4-extra{a} libmagickwand4{a} libmpg123-0{a} libmpg123-0:i386{a} 
  libncurses5:i386{a} libnetpbm10{a} libnss-winbind{a} libodbc1{a} libopenal1:i386{a} libopenexr6{a} liborc-0.4-0:i386{a} libp11-kit0:i386{a} libpam-winbind{a} 
  libpathplan4{a} libpciaccess0:i386{a} libpcre3:i386{a} libpng12-0:i386{a} libroken18-heimdal:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} 
  libselinux1:i386{a} libsm6:i386{a} libsqlite3-0:i386{a} libssl1.0.0:i386{a} libstdc++6:i386{a} libtasn1-3:i386{a} libtiff4:i386{a} libtinfo5:i386{a} 
  libunistring0:i386{a} libusb-0.1-4:i386{a} libuuid1:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libwind0-heimdal:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} 
  libxau6:i386{a} libxcb-glx0:i386{a} libxcb1:i386{a} libxcomposite1:i386{a} libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} libxext6:i386{a} 
  libxfixes3:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxt6:i386{a} 
  libxxf86vm1:i386{a} netpbm{a} odbcinst{a} odbcinst1debian2{a} p7zip{a} ttf-droid{a} ttf-umefont{a} ttf-unfonts-core{a} unixodbc{a} winbind{a} wine 
  wine-gecko1.4{a} wine-gecko1.4:i386{a} wine1.4{a} wine1.4-amd64{a} wine1.4-common{a} wine1.4-i386:i386{a} winetricks{a} zlib1g:i386{a} 
0 packages upgraded, 149 newly installed, 0 to remove and 0 not upgraded.
Need to get 168 MB of archives. After unpacking 518 MB will be used.
The following packages have unmet dependencies:
 gettext-base : Conflicts: gettext-base:i386 but 0.18.1.1-5ubuntu4 is to be installed.
 gettext-base:i386 : Conflicts: gettext-base but 0.18.1.1-5ubuntu4 is installed.
 gettext : Conflicts: gettext:i386 but 0.18.1.1-5ubuntu4 is to be installed.
 gettext:i386 : Conflicts: gettext but 0.18.1.1-5ubuntu4 is installed.
Internal error: the solver Install(grub-common:i386 1.99-21ubuntu4 <grub2-common:amd64 1.99-21ubuntu4 -> {grub-common:amd64 1.99-21ubuntu4 grub-common:i386 1.99-21ubuntu4}>) of a supposedly unresolved dependency is already installed in step 46
Internal error: the solver Install(grub-common:i386 1.99-21ubuntu4 <grub-pc-bin:amd64 1.99-21ubuntu4 -> {grub-common:amd64 1.99-21ubuntu4 grub-common:i386 1.99-21ubuntu4}>) of a supposedly unresolved dependency is already installed in step 46
Internal error: the solver Install(grub-pc:i386 1.99-21ubuntu4 <grub-gfxpayload-lists:amd64 0.6 -> {grub-pc:amd64 1.99-21ubuntu4 grub-pc:i386 1.99-21ubuntu4}>) of a supposedly unresolved dependency is already installed in step 108
open: 20; closed: 192; defer: 7; conflict: 7                                                                                                                            .Internal error: the solver Install(cups:i386 1.5.3-1 <printer-driver-hpijs:amd64 3.12.4-1 -S> {cups-ppdc:amd64 1.5.3-1 cups-ppdc:i386 1.5.3-1 cups:amd64 1.5.3-1 cups:i386 1.5.3-1 cupsddk:amd64 1.5.2-9ubuntu1 cupsddk:amd64 1.5.3-1 hpijs-ppds:amd64 3.12.4-1}>) of a supposedly unresolved dependency is already installed in step 617
Internal error: the solver Install(gvfs-daemons:i386 1.13.0-0ubuntu3 <gvfs-backends:amd64 1.13.0-0ubuntu3 -> {gvfs-daemons:amd64 1.13.0-0ubuntu3 gvfs-daemons:i386 1.13.0-0ubuntu3}>) of a supposedly unresolved dependency is already installed in step 753
Internal error: the solver Install(gvfs-daemons:i386 1.13.0-0ubuntu3 <gvfs:amd64 1.13.0-0ubuntu3 -> {gvfs-daemons:amd64 1.13.0-0ubuntu3 gvfs-daemons:i386 1.13.0-0ubuntu3}>) of a supposedly unresolved dependency is already installed in step 753
Internal error: the solver Install(gvfs-daemons:i386 1.13.0-0ubuntu3 <gvfs:amd64 1.13.0-0ubuntu3 -> {gvfs-daemons:amd64 1.13.0-0ubuntu3 gvfs-daemons:i386 1.13.0-0ubuntu3}>) of a supposedly unresolved dependency is already installed in step 753
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <gs-cjk-resource:amd64 1.20100103-3 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 796
Internal error: the solver Install(ghostscript:i386 9.05~dfsg-0ubuntu4 <ghostscript-x:amd64 9.05~dfsg-0ubuntu4 -> {ghostscript:amd64 9.05~dfsg-0ubuntu4 ghostscript:i386 9.05~dfsg-0ubuntu4}>) of a supposedly unresolved dependency is already installed in step 796
Internal error: the solver Install(bamfdaemon:i386 0.2.118-0ubuntu1 <libbamf3-0:amd64 0.2.118-0ubuntu1 -> {bamfdaemon:amd64 0.2.118-0ubuntu1 bamfdaemon:i386 0.2.118-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 826
Internal error: the solver Install(bamfdaemon:i386 0.2.118-0ubuntu1 <libbamf0:amd64 0.2.118-0ubuntu1 -> {bamfdaemon:amd64 0.2.118-0ubuntu1 bamfdaemon:i386 0.2.118-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 826
open: 65; closed: 799; defer: 25; conflict: 25                                                                                                                          oThe following actions will resolve these dependencies:

       Keep the following packages at their current version:                  
1)       gettext:i386 [Not Installed]                                         
2)       gettext-base:i386 [Not Installed]                                    
3)       libasn1-8-heimdal:i386 [Not Installed]                               
4)       libasound2:i386 [Not Installed]                                      
5)       libavahi-client3:i386 [Not Installed]                                
6)       libavahi-common3:i386 [Not Installed]                                
7)       libc6:i386 [Not Installed]                                           
8)       libcapi20-3:i386 [Not Installed]                                     
9)       libcomerr2:i386 [Not Installed]                                      
10)      libcroco3:i386 [Not Installed]                                       
11)      libcups2:i386 [Not Installed]                                        
12)      libdb5.1:i386 [Not Installed]                                        
13)      libdbus-1-3:i386 [Not Installed]                                     
14)      libdrm-intel1:i386 [Not Installed]                                   
15)      libdrm-nouveau1a:i386 [Not Installed]                                
16)      libdrm-radeon1:i386 [Not Installed]                                  
17)      libdrm2:i386 [Not Installed]                                         
18)      libexif12:i386 [Not Installed]                                       
19)      libexpat1:i386 [Not Installed]                                       
20)      libffi6:i386 [Not Installed]                                         
21)      libfontconfig1:i386 [Not Installed]                                  
22)      libfreetype6:i386 [Not Installed]                                    
23)      libgcc1:i386 [Not Installed]                                         
24)      libgcrypt11:i386 [Not Installed]                                     
25)      libgd2-xpm:i386 [Not Installed]                                      
26)      libgettextpo0:i386 [Not Installed]                                   
27)      libgif4:i386 [Not Installed]                                         
28)      libgl1-mesa-dri:i386 [Not Installed]                                 
29)      libgl1-mesa-glx:i386 [Not Installed]                                 
30)      libglapi-mesa:i386 [Not Installed]                                   
31)      libglib2.0-0:i386 [Not Installed]                                    
32)      libglu1-mesa:i386 [Not Installed]                                    
33)      libgnutls26:i386 [Not Installed]                                     
34)      libgomp1:i386 [Not Installed]                                        
35)      libgpg-error0:i386 [Not Installed]                                   
36)      libgphoto2-2:i386 [Not Installed]                                    
37)      libgphoto2-port0:i386 [Not Installed]                                
38)      libgpm2:i386 [Not Installed]                                         
39)      libgssapi-krb5-2:i386 [Not Installed]                                
40)      libgssapi3-heimdal:i386 [Not Installed]                              
41)      libgstreamer-plugins-base0.10-0:i386 [Not Installed]                 
42)      libgstreamer0.10-0:i386 [Not Installed]                              
43)      libhcrypto4-heimdal:i386 [Not Installed]                             
44)      libheimbase1-heimdal:i386 [Not Installed]                            
45)      libheimntlm0-heimdal:i386 [Not Installed]                            
46)      libhx509-5-heimdal:i386 [Not Installed]                              
47)      libice6:i386 [Not Installed]                                         
48)      libieee1284-3:i386 [Not Installed]                                   
49)      libjpeg-turbo8:i386 [Not Installed]                                  
50)      libjpeg8:i386 [Not Installed]                                        
51)      libk5crypto3:i386 [Not Installed]                                    
52)      libkeyutils1:i386 [Not Installed]                                    
53)      libkrb5-26-heimdal:i386 [Not Installed]                              
54)      libkrb5-3:i386 [Not Installed]                                       
55)      libkrb5support0:i386 [Not Installed]                                 
56)      liblcms1:i386 [Not Installed]                                        
57)      libldap-2.4-2:i386 [Not Installed]                                   
58)      libllvm3.0:i386 [Not Installed]                                      
59)      libltdl7:i386 [Not Installed]                                        
60)      libmpg123-0:i386 [Not Installed]                                     
61)      libncurses5:i386 [Not Installed]                                     
62)      libopenal1:i386 [Not Installed]                                      
63)      liborc-0.4-0:i386 [Not Installed]                                    
64)      libp11-kit0:i386 [Not Installed]                                     
65)      libpciaccess0:i386 [Not Installed]                                   
66)      libpcre3:i386 [Not Installed]                                        
67)      libpng12-0:i386 [Not Installed]                                      
68)      libroken18-heimdal:i386 [Not Installed]                              
69)      libsane:i386 [Not Installed]                                         
70)      libsasl2-2:i386 [Not Installed]                                      
71)      libsasl2-modules:i386 [Not Installed]                                
72)      libselinux1:i386 [Not Installed]                                     
73)      libsm6:i386 [Not Installed]                                          
74)      libsqlite3-0:i386 [Not Installed]                                    
75)      libssl1.0.0:i386 [Not Installed]                                     
76)      libstdc++6:i386 [Not Installed]                                      
77)      libtasn1-3:i386 [Not Installed]                                      
78)      libtiff4:i386 [Not Installed]                                        
79)      libtinfo5:i386 [Not Installed]                                       
80)      libunistring0:i386 [Not Installed]                                   
81)      libusb-0.1-4:i386 [Not Installed]                                    
82)      libuuid1:i386 [Not Installed]                                        
83)      libv4l-0:i386 [Not Installed]                                        
84)      libv4lconvert0:i386 [Not Installed]                                  
85)      libwind0-heimdal:i386 [Not Installed]                                
86)      libx11-6:i386 [Not Installed]                                        
87)      libx11-xcb1:i386 [Not Installed]                                     
88)      libxau6:i386 [Not Installed]                                         
89)      libxcb-glx0:i386 [Not Installed]                                     
90)      libxcb1:i386 [Not Installed]                                         
91)      libxcomposite1:i386 [Not Installed]                                  
92)      libxcursor1:i386 [Not Installed]                                     
93)      libxdamage1:i386 [Not Installed]                                     
94)      libxdmcp6:i386 [Not Installed]                                       
95)      libxext6:i386 [Not Installed]                                        
96)      libxfixes3:i386 [Not Installed]                                      
97)      libxi6:i386 [Not Installed]                                          
98)      libxinerama1:i386 [Not Installed]                                    
99)      libxml2:i386 [Not Installed]                                         
100)     libxpm4:i386 [Not Installed]                                         
101)     libxrandr2:i386 [Not Installed]                                      
102)     libxrender1:i386 [Not Installed]                                     
103)     libxslt1.1:i386 [Not Installed]                                      
104)     libxt6:i386 [Not Installed]                                          
105)     libxxf86vm1:i386 [Not Installed]                                     
106)     wine [Not Installed]                                                 
107)     wine-gecko1.4:i386 [Not Installed]                                   
108)     wine1.4 [Not Installed]                                              
109)     wine1.4-amd64 [Not Installed]                                        
110)     wine1.4-common [Not Installed]                                       
111)     wine1.4-i386:i386 [Not Installed]                                    
112)     winetricks [Not Installed]                                           
113)     zlib1g:i386 [Not Installed]                                          

       Leave the following dependencies unresolved:                           
114)     wine-gecko1.4 recommends wine1.4-amd64                               
115)     libgphoto2-2:i386 recommends udev:i386 (>= 0.175)                    
116)     libgphoto2-2:i386 recommends libgphoto2-l10n:i386 (>= 2.4.14-2)      
117)     libncurses5:i386 recommends libgpm2:i386                             
118)     wine1.4-i386:i386 recommends libfontconfig1:i386 | libfontconfig:i386
119)     wine1.4-i386:i386 recommends libsane:i386                            
120)     wine-gecko1.4:i386 recommends wine1.4-i386:i386                      


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
root@quantal:~#
```

---

### Post by mc4man on 2012-05-28
Both aptitude & apt-get seem to have some 'nonsense' if installing wine, at least in a 64 bit install

In apt-get's case it wants to "126 newly installed, 8 to remove", the 8 removed shouldn't be & can be re-installed after, this happens in 12.04 also 
(cdbs dh-translations gnome-common gnome-pkg-tools gtk-doc-tools intltool lintian quilt

In aptitudes case it wants to install 132 packages but shows what you posted

The idea that one needs 1/2 a GB to install wine in 64 bit seems a bit silly, but if I had to chose apt-get or aptitude I'd go with the former which should work fine

---

### Post by Cheesemill on 2012-05-28
I've just tried using apt-get and it successfully installed all 147 packages and didn't try to remove any.

It's strange that aptitude failed in this case but is usually more successful in resolving dependencies, in fact I **always** use aptitude and never use apt-get, it didn't occur to me that apt-get would be more successful.

Marking as solved (although any input on the aptitude situation would still be welcome).

---

### Post by mc4man on 2012-05-28
That's one of those which side of the fence deals, - myself almost never use aptitude, apt-get has always worked fine (the 8 removed here are an anomaly & it's not worth tracking down why.

For the most part I use synaptic for pretty much everything anyway, apt-get mainly  for sources & build-deps

---

### Post by stoneguy on 2012-06-23
Looks like WINE isn't ready yet for official QQ repos. If you're willing to walk on the wild side, get it from the unstable, unsupported ppa:ricotz/staging. The only error you should get is the lack of a compatible winetricks.

---

### Post by jbicha on 2012-06-23
Wine installs just fine here. apt-get is the Ubuntu recommended CLI tool.

Using Ricotz' staging PPA is good if you want git snapshots of the latest development code; most people shouldn't need that.

---

### Post by Starks on 2012-06-23
jbicha, is there an estimate as to when 32-bit Wine components will be buildable on 64-bit Ubuntu again?

It is pretty much impossible to test upstream patches on 12.04 and 12.10.

---

### Post by jbicha on 2012-06-24
Starks, I don't understand your question. You probably should probably file a bug (ubuntu-bug wine1.4) with more details about your specific problem. As far as I can tell, wine works fine in Ubuntu 12.04 and 12.10.

---

### Post by Starks on 2012-06-24
It's simple. It is impossible to build Wine's 32-bit libraries on 64-bit Ubuntu right now due to multiarch not working right with dev packages.

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606)

---

### Post by Jimmyfj on 2012-06-25
> **jbicha said:**
> Wine installs just fine here. apt-get is the Ubuntu recommended CLI tool.

Using Ricotz' staging PPA is good if you want git snapshots of the latest development code; most people shouldn't need that.

Just installed Wine 1.4 last night on my qq 64 bit using apt-get install. The install went smoothly without any err.msg.:D

---

