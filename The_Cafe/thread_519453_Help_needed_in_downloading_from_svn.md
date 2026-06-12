---
title: "Help needed in downloading from svn"
date: 2007-08-07
forum: The Cafe
---

### Post by @vijay@ on 2007-08-07
can anyone download this from svn
[http://tapioca-voip.sourceforge.net/wiki/index.php/Ereseva#Current_features](http://tapioca-voip.sourceforge.net/wiki/index.php/Ereseva#Current_features)

im unable to download maybe its because im behind proxy server
can anyone PLz download the files and share

---

### Post by tbroderick on 2007-08-07
Is svn.sourceforge.net  the right address? Cause it seems to be down or it doesn't exist.

---

### Post by urukrama on 2007-08-07
Make sure you have the 'subversion' package installed. Do

> sudo apt-get install subversion

if you haven't already, and try downloading it again.

---

### Post by @vijay@ on 2007-08-07
i have installed subversion but not able to download

---

### Post by urukrama on 2007-08-07
what error message does it give?

---

### Post by tbroderick on 2007-08-07
> **@vijay@ said:**
> i have installed subversion but not able to download

The addresses are wrong on that page you linked to. It should be
```

svn checkout https://tapioca-voip.svn.sourceforge.net/svnroot/tapioca-voip/trunk/tapioca-glib tapioca-glib
svn checkout https://tapioca-voip.svn.sourceforge.net/svnroot/tapioca-voip/trunk/tapioca-python tapioca-python
svn checkout https://tapioca-voip.svn.sourceforge.net/svnroot/tapioca-voip/trunk/ereseva ereseva

```

---

### Post by @vijay@ on 2007-08-07
@tbroderick

i tried to download from the new links (Can Open the Links in Firefox unlike before ones)  but getting this error ; thats may be because im behind my school firewall
here is the error im getting 
---------------------------------------------------
fvijay@vijay-desktop:~$ svn checkout [https://tapioca-voip.svn.sourceforge.net/svnroot/tapioca-voip/trunk/ereseva](https://tapioca-voip.svn.sourceforge.net/svnroot/tapioca-voip/trunk/ereseva) ereseva
svn: PROPFIND request failed on '/svnroot/tapioca-voip/trunk/ereseva'
svn: PROPFIND of '/svnroot/tapioca-voip/trunk/ereseva': could not connect to server ([https://tapioca-voip.svn.sourceforge.net](https://tapioca-voip.svn.sourceforge.net))
----------------------------------------------------

CAN U PLEASE download the three packages and upload somewhere else

---

### Post by tbroderick on 2007-08-07
> **@vijay@ said:**
> 
CAN U PLEASE download the three packages and upload somewhere else

I can try. Might take me a little while. You can also try changing  your port settings in /home/username/.subversion/servers.

---

### Post by urukrama on 2007-08-07
I get a 'host not found' message. If the address is indeed correct, their site must be down.

---

### Post by tbroderick on 2007-08-07
Here's a tar of all three, tapioca-glib, tapioca-python and ereseva checkout from svn. You still have to run autogen.sh and configure. I don't have any web space so I used zshare. If you have troubles maybe I can host it on another free site.

[tapioca-svn.tar - 9.31MB](http://www.zshare.net/download/3032680daa5df0/)

---

### Post by @vijay@ on 2007-08-08
@tbroderick  

Thanx alot da .................... :):):):):)
But do u know how to download with svn......... behind proxy server
i think mine will allow only port 443 and 80

---

### Post by tbroderick on 2007-08-08
> **@vijay@ said:**
> @tbroderick  

Thanx alot da .................... :):):):):)
But do u know how to download with svn......... behind proxy server
i think mine will allow only port 443 and 80

You can try editing ~/.subversion/servers. Under Global uncomment the http-proxy-port line and try change the port.

---

### Post by bash on 2007-08-17
When I try to run make for the ereseva package I get this error:

```
make  all-recursive
make[1]: Entering directory '/home/user/ereseva'
Making all in ereseva
make[2]: Entering directory '/home/user/ereseva/ereseva'
pylint --indent-string="    " --max-args=6 --max-public-methods=35 ereseva.py
/bin/bash: pylint: command not found
make[2]: *** [ereseva.py] Error 127
make[2]: Exiting directory '/home/user/ereseva/ereseva'
make[1]: *** [all-recursive] Error 1
make[1]: Exiting directory '/home/user/ereseva'
make: *** [all] Error 2
```

Anybody knows help?

---

### Post by Frak on 2007-08-17
```
sudo aptitude install pylint pylint-dev pylint-dbg
```
remake and see if it works :)

---

### Post by @vijay@ on 2007-08-19
> **tbroderick said:**
> You can try editing ~/.subversion/servers. Under Global uncomment the http-proxy-port line and try change the port.

thanx a lot ; just now only saw the message ; IT WORKED
THANX ALOT

---

### Post by ntetreau on 2007-08-30
Trying to compile, I get this error trying to compile tapioca-python:

```

pygtk-codegen-2.0 --prefix tapiocaclient \
        --register /gdk-types.defs \
        --register /gtk-types.defs \
        --override tapiocaclient.override \
        tapiocaclient.defs > tapiocaclient.c
Traceback (most recent call last):
  File "/usr/share/pygtk/2.0/codegen/codegen.py", line 1712, in <module>
    sys.exit(main(sys.argv))
  File "/usr/share/pygtk/2.0/codegen/codegen.py", line 1670, in main
    p.startParsing()
  File "/usr/share/pygtk/2.0/codegen/scmexpr.py", line 113, in startParsing
    for statement in statements:
  File "/usr/share/pygtk/2.0/codegen/scmexpr.py", line 27, in parse
    fp = open(filename, 'r')
IOError: [Errno 2] No such file or directory: '/gdk-types.defs'
make[2]: *** [tapiocaclient.c] Error 1
make[2]: Leaving directory `/home/nt271/temp/ereseva/tapioca-python/tapioca'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nt271/temp/ereseva/tapioca-python'
make: *** [all] Error 2


```

---

### Post by glacierre on 2007-12-16
Installing python-gtk-1.2 solved that problem for me.

---

