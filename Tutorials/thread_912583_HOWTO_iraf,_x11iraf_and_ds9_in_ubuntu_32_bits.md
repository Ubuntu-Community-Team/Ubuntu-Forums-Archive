---
title: "HOWTO: iraf, x11iraf and ds9 in ubuntu 32 bits"
date: 2008-09-06
forum: Tutorials
---

### Post by orlox on 2008-09-06
Hi! For those who don't know (probably the most) iraf is a software used by astronomers to reduce and process data (actually it has many more uses but this is the one I use most...). So probably, if you came across this by accident, you probably don't need a program that does this...

For those of you who NEED this, and can't get to install it, here's the howto:):

First of all, in case everything fails, you can use the installation guide that can be downloaded from [here]("http://iraf.noao.edu/iraf/ftp/iraf/v214/PCIX/pciraf.ps.gz").

Now, prerequisites:
[LIST]
[*]Universe repository enabled. In case not, and if you don't know what this means, check many of the howtos on how to do this
[*]Working internet connection
[*]you must be a sudoer (meaning this, that you can use sudo)
[/LIST]

So let's begin installing this things

[SIZE="5"]IRAF[/SIZE]
The version of iraf that we will install is v214. This one, unlike version v212 comes with the ecl terminal which allows autocompletion and using the up key to check previous commands.

Okay, so, to begin with, we will install the tcsh package (that's in the universe repository)
```

sudo apt-get install tcsh

```
Next, we make a folder were all of the iraf downloads will go (in order to keep things neat). Please keep yourself in the same terminal:
```

mkdir ~/iraf
cd ~/iraf

```
Then, we download the iraf files. These are:
[LIST]
[*]as.pcix.gen.gz, the architecture independent files
[*]ib.lnux.x86.gz, the linux dependent base files
[*]nb.lnux.x86.gz, the linux dependent noao  files
[/LIST]
In the download directions, the v214 folder could be replaced by a more recent version in case it exists:
```

wget http://iraf.noao.edu/iraf/ftp/iraf/v214/PCIX/as.pcix.gen.gz
wget http://iraf.noao.edu/iraf/ftp/iraf/v214/PCIX/ib.lnux.x86.gz
wget http://iraf.noao.edu/iraf/ftp/iraf/v214/PCIX/nb.lnux.x86.gz

```
Next, I make iraf's directory tree:
```

sudo mkdir -p /iraf/{irafbin/{bin.linux,noao.bin.linux},iraf/local}

```
Next i add the iraf user (this will ask you many things. The only important one is the password, the rest could be left in blank. The user is added at the admin group so he can sudo when installing iraf):
```

sudo adduser iraf --home /iraf/iraf/local --shell /bin/csh --ingroup admin

```
And I move the downloaded files to the /iraf/iraf directory, and grant all permissions on the directories to the iraf user:
```

sudo mv ~/iraf/* /iraf/iraf
sudo chown iraf -R /iraf

```
Now I login as the iraf user:
```

su iraf

```
We extract the iraf files:
```

cd /iraf/iraf
cat /iraf/iraf/as.pcix.gen.gz | zcat | tar -xpf -
cd /iraf/iraf/bin.linux
cat /iraf/iraf/ib.lnux.x86.gz | zcat | tar -xpf -
cd /iraf/iraf/noao/bin.linux
cat /iraf/iraf/nb.lnux.x86.gz | zcat | tar -xpf -

```
And we remove the unneccesary files:
```

rm /iraf/iraf/as.pcix.gen.gz
rm /iraf/iraf/ib.lnux.x86.gz
rm /iraf/iraf/nb.lnux.x86.gz

```
And we prepare things for the installation (from this point it is essential to keep the same terminal open until the end of the installation):
```

setenv iraf /iraf/iraf
cd $iraf/unix/hlib/
source irafuser.csh

```
We first test the install, to do this we run (from the same terminal of the step before):
```

sudo ./install -n

```
Prompting yes to everything should be enough. In any case, the proccess can get stuck in a loop where it asks if it should configure iraf-networking, fail at trying to configure it, and asking again. The error message you should receive is:
```

Checking that iraf networking is properly enabled ...      os.zgtenv:
cannot open &#8216;/usr/include/iraf.h&#8217;
[ FAIL ]
   ***  The NETSTATUS task claims that networking is disabled.
   ***  Please contact site support (iraf@noao.edu) with questions
   ***  or check the Site Manager&#8217;s Guide for details on how to
   ***  properly configure networking.


```
To solve this simply say no at this point.

If the installation test went fine, you can install everything by omitting the -n argument:
```

sudo ./install

```
Having installed iraf successfully, you can exit from the iraf user's shell bi doing (closing the terminal will work too:)):
```

exit

```
[SIZE="5"]x11iraf[/SIZE]
Next we install x11iraf which is needed for irafs graphical support. The version to be installed is 1.3.1, but this could be replaced for a newer one with no problem only by changing the download.

We download x11iraf files to our downloads folder:
```

cd ~/iraf
wget http://iraf.noao.edu/iraf/ftp/iraf/x11iraf/x11iraf-v1.3.1/x11iraf-v1.3.1-bin.linux.tar.gz

```
We extract it and install it:
```

cat x11iraf-v1.3.1-bin.linux.tar.gz | gunzip | tar -xf -
sudo ./install

```
[SIZE="5"]ds9[/SIZE]
The proccess is simple, download the file, extract it, and copy and give write permission to the binary. We install with this version 5.6 of ds9, but just as in the other steps, this can easily be updated by changing the download address:
```

cd ~/iraf
wget http://hea-www.harvard.edu/saord/download/ds9/linux/ds9.linux.5.6.tar.gz
tar -zxf ds9.linux.5.6.tar.gz
sudo mv ds9 /usr/local/bin
sudo chmod +x /usr/local/bin/ds9

```
[SIZE="5"]Start-up script[/SIZE]
For convenience, we will make a start-up script (created by michael hutchinson [http://mjhutchinson.com/](http://mjhutchinson.com/)) that will open an xgterm with an ecl promt and ds9. We use gedit or this, but any text editor (for example kate in kde or vim) could be used:
```

sudo gedit /usr/local/bin/irafshell

```
And next we add this to the file:
```

#!/bin/bash
PID=`pidof ds9`
if [ ! $PID ]; then
ds9 &
fi
pushd ~/iraf > /dev/null
xgterm -iconic -geometry 80x24 -sb -title "IRAF" -bg "black" -fg "green" -e "ecl" &
popd > /dev/null

```
Here, the -bg and -fg options indicate respectively background and font colors for the xgterm where iraf will be run. Some of the available colors are lemon chiffon, black, darkslategrey, linen, red, green, blue, cyan, yellow, purple, magenta and slategray. I personally prefer the black on green layout...

Then, add execution permission to the script:
```

sudo chmod +x /usr/local/bin/irafshell

```
With this, iraf can be run just by running the command irafshell.
[SIZE="5"]Running iraf[/SIZE]
First, I clean the ~/iraf folder (THIS COMMAND WILL DELETE EVERYTHING ON THE FOLDER):
```

rm -rf ~/iraf/*

```
to run iraf, we create the login.cl and use irafshell command. When mkiraf asks for terminal type, select xgterm.
```

cd ~/iraf
mkiraf
irafshell

```
If you get the error "xgterm: no available ptys", Then follow this steps (if iraf started correctly, then you dont need to this):
```

wget ftp://iraf.noao.edu/pub/xgterm.fedora
sudo mv xgterm.fedora /usr/local/bin/xgterm
sudo chmod +x /usr/local/bin/xgterm

```
And now you should be able to run the command irafshell with no problems.
[SIZE="5"]Icon![/SIZE]
This is a suggestion made by Elias Pizarro. You can download the iraf icon and use it to show an iraf icon in your application list wich will execute the irafshell script. First, download the iraf icon:
```

cd /usr/share/pixmaps/
sudo wget http://iraf.noao.edu/iraf/web/images/iraf.gif

```
Then, create the desktop entry:
```

gedit ~/.local/share/applications/iraf.desktop

```
And add to the file this:
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Terminal=false
Type=Application
Categories=Application;Office;Astronomy;
Exec=irafshell
Name=IRAF
Comment=Image reduction and analysis facility
Icon=/usr/share/pixmaps/iraf.gif

```
and voila! suggestions, corrections, etc... are welcome...

see you later!

---

### Post by ajmorris on 2008-09-06
hi there,
just something i noticed with your mkdir commands, instead of doing a long winded way:

```
sudo mkdir /iraf
sudo mkdir /iraf/iraf
sudo mkdir /iraf/iraf/local

```you can do:
```
sudo mkdir -p /iraf/iraf/local
```and instead of:
```
mkdir /iraf/irafbin
mkdir /iraf/irafbin/bin.linux
mkdir /iraf/irafbin/noao.bin.linux
```you could do:
```
mkdir -p /iraf/{,irafbin/{bin.linux,noao.bin.linux}}
```It is handy for not having to repeditively type mkdir etc

AJ

---

### Post by orlox on 2008-09-07
Thanks for the tip. I'll edit the howto to do it that way.

---

### Post by favilac on 2008-09-07
I have an installer for IRAF that includes

IRAF                 2.14
STSDAS               3.8
TABLES               3.8
PyRAF                1.5
DS9                  5.2
X11IRAF              1.5
WCSTOOLS             3.7.0
Telarchive           1.4

You only need the universe and multiverse repos enabled.

The .iso which includes the files, installer and uninstaller is in
[http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso](http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso)

To install just do a 'sh install.sh' and when in ends, in your home directory do a mkiraf and pick xgterm as your terminal.

It's all.

---

### Post by orlox on 2008-09-07
> **favilac said:**
> I have an installer for IRAF that includes

IRAF                 2.14
STSDAS               3.8
TABLES               3.8
PyRAF                1.5
DS9                  5.2
X11IRAF              1.5
WCSTOOLS             3.7.0
Telarchive           1.4

You only need the universe and multiverse repos enabled.

The .iso which includes the files, installer and uninstaller is in
[http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso](http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso)

To install just do a 'sh install.sh' and when in ends, in your home directory do a mkiraf and pick xgterm as your terminal.

It's all.

Well, guess thats another way to do it :P...

question...where do you get x11iraf 1.5????

---

### Post by favilac on 2008-09-08
Actually it's a beta ( x11iraf-v1.5DEV), but it's been a beta for at least three years now. Heh, maybe more because a remember that it fixed the issues it had with redhat 9 and the new kernel it used.



I got it from iraf.net (the site is down at the moment).

---

### Post by astroumut on 2008-09-08
> **favilac said:**
> I have an installer for IRAF that includes

IRAF                 2.14
STSDAS               3.8
TABLES               3.8
PyRAF                1.5
DS9                  5.2
X11IRAF              1.5
WCSTOOLS             3.7.0
Telarchive           1.4

You only need the universe and multiverse repos enabled.

The .iso which includes the files, installer and uninstaller is in
[http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso](http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso)

To install just do a 'sh install.sh' and when in ends, in your home directory do a mkiraf and pick xgterm as your terminal.

It's all.



That's great favilac, it took hours for me to install IRAF , but i wasn't succesful. With your installer it is quite easier and the nice thing is working. Thanks a lot...

---

### Post by favilac on 2008-09-08
No problem :)

I forgot to mention that the installer creates an alias in /usr/local/bin which launches an xgterm running ecl, and the ds9 viewer. The alias is called 'iraf'.

Also, the installer is easy to modify so it can run in a 64 bit system.
You only need to edit the DEPS field to include the 32 bits libraries.

---

### Post by emtilt on 2008-10-12
favilac:

I don't know if you'll see this, but your install script was very helpful. I got IRAF running within a couple minutes, after failing to get it running when I tried to install it on my own. So thanks a bunch for making it. 

Unfortunately, I can't seem to get PyRAF working. That portion of the install script returns boatloads of errors. I'm running xubuntu, but that shouldn't matter (though I've not used any Ubuntu distros before now, I was under the impression that xubuntu differed only in that it uses Xfce). If you can shed any light as to what the problem might be, I'd really appreciate it. You can see a log of the output for install here, if you'd like: [http://uploaded.interestingnonetheless.net/emtilt/logubuntuiraf.txt](http://uploaded.interestingnonetheless.net/emtilt/logubuntuiraf.txt)

---

### Post by favilac on 2008-10-13
Hi. I don't have an amd64 install handy, but it seems that you don't have libc6-dev installed. I think that because i had installed earlier, didn't realize that you really need to build pyraf.

 However, because as I said i don't have a 64 bit install (i'll try to install it tomorrow night), I'm not totally sure you need libc6-dev or libc6-dev-amd64.

 I'm betting on the later.

 Try installing libc6-dev-amd64 first and try again. If it works, well, you will save me from a double-reinstall ;)

---

### Post by emtilt on 2008-10-13
I'm running a 32 bit system, not an amd64 bit one. I will try installing libc6-dev, though, and see if that resolves the problem.

---

### Post by emtilt on 2008-10-13
I've added libc6-dev and everything worked smoothly. Thank you so much for your script and your assistance.

---

### Post by favilac on 2008-10-14
Thanks for the info.
 
I haven't had the chance to do a reinstall, but because it was so simple i'll have the updated installers and iso tonight.

If you already have the files, the only change will be to update the DEPS field to include libc6-dev and libc6-amd-dev.

---

### Post by super zach on 2008-11-05
thanks this post was veeeeeeeeeeerrrrrrrrry helpful!:KS

---

### Post by rene8 on 2009-01-30
orlox & favilac, thanks so much for your posts!
We, Astronomy students, usually have a lot of trouble installing IRAF.

favilac: how can I do to install the new 2.14.1 version using your script?
Por cierto... ¿eres de la Universidad de Sonora?

---

### Post by rene8 on 2009-01-30
I've just seen that the up-to-date .iso contains 2.14.1 version!
It installed itself in a minute, which is record time for iraf, so:
THANK YOU VERY MUCH!

---

### Post by favilac on 2009-01-30
I'm glad it has helped you. I know how painful can IRAF be to install ( I started with it around '98 with a copy of RH 6.0!).

 The next updated .iso is going to be released as soon as posible, as the new x11iraf 2.0 is released.

 Rene8>
 Si, soy de la UniSon. CUando Heinz era el jefe de uds. estuve a punto de irme a trabajar alla como encargado de computo, pero todavia no terminaba mi tesis de lic. Ya hace un buen de tiempo! :D

---

### Post by Blueball32 on 2009-05-13
Didn't work for me...had an error at the mkiraf-part. I followed another installguide (v2.13BETA) which worked...;)

---

### Post by rene8 on 2009-07-16
I just installed IRAF on my new laptop running on jaunty, using the .iso provided by favilac.

In my case (my laptop has two AMD 64-bit processors, and so I installed the Ubuntu 64-bit version), the package libc6-dev-amd64 is nowhere to be found, so I simply deleted it from the list of packages on the install-ubuntu64.sh file and install IRAF as normal.

This worked perfectly, so I assume that libc6-dev-amd64 is not needed anymore for the 64-bit install.

c u!

---

### Post by timothyarnold on 2009-09-22
favilac:

Thanks so much for creating this installer. It's incredibly easy to use, and saves a TON of time. 

I recently attempted to use the most recent ISO to install IRAF etc. on an amd64 install of Ubuntu 9.04. 

Everything worked smoothly until the end, when I ran into some troubles with PyRAF (and, it seems, WCSTOOLS, though I'm not sure). 

This is the error message I received at the end of the install:

```

      Installing PyRAF

/iraf/extern/pyraf/pyraf-1.7/stsci_distutils_hack.py:258: DeprecationWarning: os.popen3 is deprecated.  Use the subprocess module.
  (sin, sout, serr) = os.popen3(cmd)
In function ‘strncat’,
    inlined from ‘MyXlibIOErrorHandler’ at src/xutil.c:64:
/usr/include/bits/string3.h:153: warning: call to __builtin___strncat_chk might overflow destination buffer

        Installing pywcs

wcsulex.l: In function ‘wcsulex’:
wcsulex.l:988: warning: statement with no effect
wcsulex.l: At top level:
wcsulex.c:8709: warning: ‘input’ defined but not used
wcsutrn.l: In function ‘wcsutrn’:
wcsutrn.l:353: warning: statement with no effect
wcsutrn.l: At top level:
wcsutrn.c:4964: warning: ‘input’ defined but not used
wcslib-4.3/C/prj.c:364: warning: function declaration isn’t a prototype
wcslib-4.3/C/tab.c:1146: warning: function declaration isn’t a prototype
wcslib-4.3/C/tab.c:1170: warning: function declaration isn’t a prototype
wcslib-4.3/C/tab.c:1235: warning: function declaration isn’t a prototype
wcspih.l: In function ‘wcspih’:
wcspih.l:1019: warning: statement with no effect
wcspih.l: At top level:
wcspih.c:9976: warning: ‘input’ defined but not used
wcspih.c: In function ‘wcspih’:
wcspih.l:151: warning: ‘errmsg’ may be used uninitialized in this function
wcspih.l:151: note: ‘errmsg’ was declared here
src/pywcs.c:717: warning: ‘_state’ defined but not used

        Installing telarchive


        Installing Menu Items to
           the Education Category




      IRAF install has finished.

```


IRAF seems to be working fine, along with DS9 and most of the python libraries. I'd very much appreciate any help!

Thanks!

Tim

---

### Post by RaQua on 2009-10-16
Many many many thanks to favilac! 

IRAF installed in a couple of minutes (maybe less...!)

---

### Post by Cosmos42 on 2010-03-15
Okay, 'wget [http://hea-www.harvard.edu/saord/download/ds9/linux/ds9.linux.5.6.tar.gz](http://hea-www.harvard.edu/saord/download/ds9/linux/ds9.linux.5.6.tar.gz)' returns an error 404 message.  After some searching, ds9 is now v 6.0, so just replace the '5.6' with '6.0' and it works.

---

### Post by dmaitra on 2010-04-30
It looks like the latest release of Ubuntu (10.04, Lucid Lynx) does not contain gfortran-4.2 anymore :(, so favilac's install scripts fail.  Does anyone have any tweaks that might work?

Thanks,
Dipankar

---

### Post by rene8 on 2010-05-01
> **dmaitra said:**
> It looks like the latest release of Ubuntu (10.04, Lucid Lynx) does not contain gfortran-4.2 anymore :(, so favilac's install scripts fail.  Does anyone have any tweaks that might work?

Thanks,
Dipankar

Try installing gfortran before running the script;
```
sudo apt-get install gfortran
```

Cheers!

---

### Post by dmaitra on 2010-05-02
Actually I already have gfortran installed.  However the default (that gets installed via sudo aptitude install gfortran) is now gfortran-4.4.  The iraf install script is specifically looking for v4.2, and there is no gfortran-4.2 anymore for Ubuntu 10.04.

---

### Post by Isaac12 on 2010-05-02
Hi all together! 
I just updated to Ubuntu 10.04. To get iraf working I copied all files from the .iso to a folder where I can write an edited the install-ubuntu.sh. There I exchanged 4.2 by 4.4. for the gfortran package. ECL seems to work fine. 
Now there are some problems with pyraf: 

Traceback (most recent call last):
  File "/usr/local/bin/pyraf", line 62, in <module>
    from pyraf import doCmdline, _use_ipython_shell, iraf, __version__
  File "/usr/local/lib/python2.6/dist-packages/pyraf/__init__.py", line 29, in <module>
    import irafimport
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 102, in <module>
    iraf = _originalImport('iraf', globals(), locals(), [])
  File "/usr/local/lib/python2.6/dist-packages/pyraf/iraf.py", line 8, in <module>
    from iraffunctions import *
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/local/lib/python2.6/dist-packages/pyraf/iraffunctions.py", line 53, in <module>
    import numpy, sscanf, minmatch, subproc, wutil
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/__init__.py", line 130, in <module>
    import add_newdocs
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/add_newdocs.py", line 9, in <module>
    from lib import add_newdoc
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/lib/__init__.py", line 4, in <module>
    from type_check import *
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/lib/type_check.py", line 8, in <module>
    import numpy.core.numeric as _nx
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/core/__init__.py", line 6, in <module>
    import umath
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
TypeError: _irafImport() takes at most 4 arguments (5 given)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 48, in apport_excepthook
    if not enabled():
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 21, in enabled
    import re
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
TypeError: 'NoneType' object is not callable

Original exception was:
Traceback (most recent call last):
  File "/usr/local/bin/pyraf", line 62, in <module>
    from pyraf import doCmdline, _use_ipython_shell, iraf, __version__
  File "/usr/local/lib/python2.6/dist-packages/pyraf/__init__.py", line 29, in <module>
    import irafimport
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 102, in <module>
    iraf = _originalImport('iraf', globals(), locals(), [])
  File "/usr/local/lib/python2.6/dist-packages/pyraf/iraf.py", line 8, in <module>
    from iraffunctions import *
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/local/lib/python2.6/dist-packages/pyraf/iraffunctions.py", line 53, in <module>
    import numpy, sscanf, minmatch, subproc, wutil
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/__init__.py", line 130, in <module>
    import add_newdocs
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/add_newdocs.py", line 9, in <module>
    from lib import add_newdoc
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/lib/__init__.py", line 4, in <module>
    from type_check import *
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/lib/type_check.py", line 8, in <module>
    import numpy.core.numeric as _nx
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
  File "/usr/lib/python2.6/dist-packages/numpy/core/__init__.py", line 6, in <module>
    import umath
  File "/usr/local/lib/python2.6/dist-packages/pyraf/irafimport.py", line 34, in _irafImport
    return _originalImport(name, globals, locals, fromlist)
TypeError: _irafImport() takes at most 4 arguments (5 given)
>>> 


 Any ideas?

---

### Post by favilac on 2010-05-17
Hi Everybody.

  I haven't had the time to update the scripts to make it work with the new Ubuntu release. However:
 
  1.- gfortran. The requirement in the script for version 4.2 it's because Xvista. If you don't use or need Xvista, edit the install-ubuntu.sh file and delete the gfortran-4.2 in the DEPS field. That's all.

  2.- Pyraf. This is case of a mismatch of versions. The pyraf included in the installer is the last one that works in Ubuntu 8.04 and Debian Lenny. The newest pyraf works in Ubuntu 10.04 but it doesn't in 8.04. So ignore the errors and install the newest version from STSCI.

  When will an updated version of the installer will be ready? Whenever of this happens first:
  a) IRAF 2.1 5 is ready.
  b) Ubuntu 10.04.1 is ready.
  c) Debian Squeeze is ready.

  I hope to have a unified installer by then (debian/ubuntu i386/amd64).

  Any more questions, you can send it to my mail (it's in the README file!).

---

### Post by tonetty on 2010-07-04
Hi everybody,

I installed IRAF and DS9  without any troubles in Karmic Koala, then I upgrade to Lucid Lynx (both on 32 bits machine). Everything is ok but IMEXAMINE: no cursor blinking on DS9 display, almost no interaction with the graphics display.
Has anyone met the same problem? I've just seen something similar in iraf.net but I didn't find it very useful.

---

### Post by tonetty on 2010-07-09
I managed the IMEXAMINE trouble with a simple mkiraf from the IRAF user but now I've another problem with my HP F4280 all-in-one Deskjet printer...

When  I use SPLOT or IMPLOT and then I try to make some hardcopies with :.snap some strange message appears (see snapshot [http://dl.dropbox.com/u/4505727/screen](http://dl.dropbox.com/u/4505727/screen)  ) and nothing is printed even if hplip notify me that a job has been started and completed...

I found that any job was a 0K files

 it seems  that SGIDSPATCH  is ok and that the printer is ok with other software...

Please, can somebody help me?

---

### Post by shouravv on 2010-10-18
I first installed iraf a long time (5.10 era, I think) ago and  recently (10.04) installed it on my new 64-bit machine, both times using this page as a guide -

[http://geco.phys.columbia.edu/~rubab/iraf/iraf_step_by_step_installation](http://geco.phys.columbia.edu/~rubab/iraf/iraf_step_by_step_installation)

and faced almost no problem. However, it seems to have been written for absolute beginners and has some broken links which you'll need to work out for yourself.

---

### Post by RobinLKM on 2010-10-27
Dear orlox,

Thank you for your precious contribution. Though I still spent about a day as I am still not familiar with linux commands at all. Also, I don't want to spoil my dignity by going to the packed IRAF which requires very little attention. :P

By the way, there is one line for the **ICON** part needed to be modified.

```
gedit ~/.local/share/applications/iraf.desktop
```into 

```
gedit usr/share/applications/iraf.desktop
```ps: I used this

```
sudo gedit usr/share/applications/iraf.desktop
```~/usr didn't work for me since my home directory leads me to /home/<username>

---

### Post by favilac on 2010-11-09
Finally!!

   There is a new version of the installer for Ubuntu 10.04. It also will be compatible with Debian Squeeze.

   There is a unified script for both distribution and 32 and 64 bits. However you must be root to run it (just do a sudo -s first in Ubuntu).

   STSDAS and TABLES updated to 3.12
   PyRAF now is version 1.9 and DS9 is 6.2.
   The X11Iraf is the latest 2.0 beta (ximtool now can run in a 24 bit display).

   The new .iso file is in:

[http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")

   An uninstall of the previous version is recomended.

---

### Post by RobinLKM on 2010-11-09
> **favilac said:**
> Finally!!

   There is a new version of the installer for Ubuntu 10.04. It also will be compatible with Debian Squeeze.

   There is a unified script for both distribution and 32 and 64 bits. However you must be root to run it (just do a sudo -s first in Ubuntu).

   STSDAS and TABLES updated to 3.12
   PyRAF now is version 1.9 and DS9 is 6.2.
   The X11Iraf is the latest 2.0 beta (ximtool now can run in a 24 bit display).

   The new .iso file is in:

[http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")

   An uninstall of the previous version is recomended.

Cool! Thanks a lot. May I know what do you use to pack all the commands into an automatic installer?

---

### Post by favilac on 2010-11-09
> Cool! Thanks a lot. May I know what do you use to pack all the commands 
> into an automatic installer? 

  Tarballs, lots of little shell scripts and a main shell script to run it all.

  This way is easier to update each package individually, and to debug the problems.

---

### Post by gecker on 2011-01-27
Hi,

I am trying to install iraf 2.15 on Ubuntu 10.10 64-bits according to[COLOR=Red] [http://geco.phys.columbia.edu/~rubab/iraf/iraf_step_by_step_installation_64bit](http://geco.phys.columbia.edu/~rubab/iraf/iraf_step_by_step_installation_64bit)[/COLOR] by cut & pasting commands line by line.

When I get to the install command, this is what happens:

[COLOR=Red]/iraf/iraf/unix/hlib# ./install
./install: Permission denied.

[COLOR=Black]this, after I checked that I am root and install is executable as shown below.[/COLOR]
[/COLOR]
/iraf/iraf/unix/hlib# whoami
root

/iraf/iraf/unix/hlib# chmod a+x install

I am new to this forum and hope I am in the right place. My apologies if not :(.

Cheers,

gecker

---

### Post by rene8 on 2011-01-27
@gecker:
I'm no expert but, have you checked if all the directories you're going to write into have writing permissions?

---

### Post by gecker on 2011-01-27
rene8: 
Thank you for your response. All directories I checked files were executable except for lib*.so.x.x.x files, which I guess are supposed to be like that... or not??? I wouldn't dare to chmod them unless I am told that it is perfectly OK.

Cheers,

gecker

---

### Post by rene8 on 2011-01-27
@gecker:
Mmmm... sorry; I am really not an expert.

Maybe you could try using the script user favilac has prepared (link below) - it works smoothly and easily in both 32 and 64-bit systems.

[http://www.astro.uson.mx/favilac/dow...RAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/dow...RAF_Ubuntu.iso")

Cheers!

---

### Post by gecker on 2011-01-28
rene8:

Thanks , I tried but I do not have permission for this site :-( 

Cheers,

gecker

---

### Post by Gaba_p on 2011-02-04
Hi,

I'd also like to download the script, but I can't access because of lack of permission. Could you upload it to some external server (Megaupload, GoogleDocs, Dropbox, etc...)?

Thanks a lot.

Cheers!

---

### Post by favilac on 2011-02-04
The link that Rene8 put is incomplete.

The correct address for my script is

[http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")

---

### Post by Gaba_p on 2011-02-05
Hi favilac,

thank you very much for the correct link to the script (and for writing it :)
One question: can I install IRAF without creating a new 'IRAF' user? I'd like to install it in my current account, and not have to switch back and forth whenever I need to use it.
My idea is to be able run the 'mkiraf' command inside my Dropbox folder (under my current user session), so as to keep everything (login.cl, loginuser.cl files, 'uparm' dir and the images I'll be working on) synced with my laptop.

Cheers!

Gabriel

---

### Post by favilac on 2011-02-05
The iraf user is needed in the 2.14 series for administration purposes only. You don't have to be the user "iraf" to run the software.

You need to run the mkiraf comand in the $HOME directory of the users to initialize some parameters with login.cl file and the uparm/ directory.

In the new 2.15 version, the iraf user is not used anymore.

---

### Post by TonySilva on 2011-03-16
Great tutorial.
@favilac

What is the default password to Iraf administrator?
Like @Gaba_p says Is there any method to install IRAF  without creating a new 'IRAF' user?

Thank you

---

### Post by favilac on 2011-03-16
The IRAF user doesn't have a password. It's created at install time with the flag --disabled-password.

  The new version of IRAF 2.15 doesn't need this account, but 2.14 still requires it.

---

### Post by Davestom on 2011-03-24
Just wanted to say thanks! I have forwarded this guide to my fellow astronomers. For the ones searching a short version of this post:
> sudo apt-get install libc6-dev
wget [http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso](http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso)
mount -o loop -t iso9660 'Where is your iso?' 'Where to mount'
sh install.sh
cd ~
mkiraf
type: xgterm


This works on a fresh install of 10.10 ubuntu on VMplayer.

---

### Post by jbullis on 2013-04-10
Trying to follow the code here to install iraf using this iso but i keep running into problems...

mount -o loop -t iso9660 ~/Downloads/IRAF_Ubuntu.iso  ~/IRAF
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I should also add that im currently using 12.04 LTS

---

