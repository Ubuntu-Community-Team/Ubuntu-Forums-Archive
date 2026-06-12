---
title: "Beagle Problems"
date: 2005-05-20
forum: Ubuntu Backports
---

### Post by bored2k on 2005-05-20
> ~$ best

** (/usr/lib/beagle/Best.exe:20407): WARNING **: The following assembly referenc ed from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=7)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/beagle).


** (/usr/lib/beagle/Best.exe:20407): WARNING **: The class Gecko.WebControl coul d not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x01000034)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be re ached
aborting...
Aborted and > :~$ beagled
rafael@noir:~$
Unhandled Exception: System.DllNotFoundException: libMonoPosixHelper.so
in (wrapper managed-to-native) Mono.Posix.Syscall:map_Mono_Posix_FileMode (Mono. Posix.FileMode)
in [0x00002] (at /home/jdong/dev/mono-1.1.7/mcs/class/Mono.Posix/Mono.Posix/Sysc all.cs:257) Mono.Posix.Syscall:chmod (System.String path, FileMode mode)
in <0x000e9> Beagle.Daemon.PathFinder:get_StorageDir ()
in <0x0000d> Beagle.Daemon.PathFinder:get_LogDir ()
in <0x00286> Beagle.Daemon.BeagleDaemon:Main (System.String[] args) 

Since I found now way around this, here's all I could do
> sudo apt-get remove --purge beagle -y 
Is there any way to fix this so I can give Beagle another shot ?  ](*,)

---

### Post by Majlo on 2005-05-20
Did you put these lines in ~/.bashrc ?

...
...
export GOOGLE_WEB_API_KEY=<Your own google api key> 
export LD_LIBRARY_PATH=/usr/lib/ #This is where the libcamel package should installed its .so file.
export BEAGLE_DEBUG=lucene #This will start beagle with debugging
...
...

GOOGLE_WEB_API_KEY you find at[ http://api.google.com/createkey](http://api.google.com/createkey)  Google Api Key .
Try this

---

### Post by bored2k on 2005-05-20
[QUOTE=Majlo]Did you put these lines in ~/.bashrc ?

...
...
export GOOGLE_WEB_API_KEY=<Your own google api key> 
export LD_LIBRARY_PATH=/usr/lib/ #This is where the libcamel package should installed its .so file.
export BEAGLE_DEBUG=lucene #This will start beagle with debugging
...
...

GOOGLE_WEB_API_KEY you find at[ http://api.google.com/createkey](http://api.google.com/createkey)  Google Api Key .
Try this[/QUOTE]
 Well no  one told me I had to.. I'll try that in a bit

---

### Post by jdong on 2005-05-20
Read the backport announcement, I provided a list of packages that **YOU MUST INSTALL MANUALLY,** because the package SUCKS at defining its own dependencies.

---

### Post by jdong on 2005-05-20
Also, make sure your root/home filesystems are mounted with Extended Attributes (mount option xattr)

---

### Post by bored2k on 2005-05-20
[QUOTE=jdong]Read the backport announcement, I provided a list of packages that **YOU MUST INSTALL MANUALLY,** because the package SUCKS at defining its own dependencies.[/QUOTE]
 And just where is this announcement :? ?

---

### Post by jdong on 2005-05-20
[http://ubuntuforums.org/showthread.php?t=35360](http://ubuntuforums.org/showthread.php?t=35360)

---

### Post by bonifacio on 2005-05-20
I followed jdong's post on that link but somehow I still do have some missing dependencies so right after that I followed the one on beaglewiki's site for hoary and everything seems to be in order now.

Please refer to that thread that jdong's pointed out.

---

### Post by bored2k on 2005-05-20
[QUOTE=bonifacio]I followed jdong's post on that link but somehow I still do have some missing dependencies so right after that I followed the one on beaglewiki's site for hoary and everything seems to be in order now.

Please refer to that thread that jdong's pointed out.[/QUOTE]
 Ok now it's working through [http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)


> DEBUG: Starting task Crawling ~/.gaim/logs to find new logfiles
DEBUG: Finished task Crawling ~/.gaim/logs to find new logfiles in .01sBut it's just indexing gaim files? I did set fstab attributes. What is wrong?

Nevermind. After [http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto](http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto) , it worked :D.

---

### Post by TravisNewman on 2005-06-03
[QUOTE=jdong]Also, make sure your root/home filesystems are mounted with Extended Attributes (mount option xattr)[/QUOTE]
sure about that? I get a load of errors on bootup, no to mention a totally unusable system if I try that.

---

### Post by infinito on 2005-06-03
Everyone trying to get Beagle to work on Ubuntu Hoary should read this Howto I wrote:
[http://infinito.f2o.org/blog/?p=28](http://infinito.f2o.org/blog/?p=28)

Lot of people from this forum (and others) tried it succesfully.

---

### Post by jdong on 2005-06-03
[QUOTE=panickedthumb]sure about that? I get a load of errors on bootup, no to mention a totally unusable system if I try that.[/QUOTE]

The actual option is **user_xattr**, and I'm SURE it works with reiserfs and ext3, and I'm SURE it doesn't work with ext2 (default Kernel).

XFS's extended attribute support is weird, and I haven't tried it. (They used to have lots of SELinux issues)

Reiser4 -- I'm SURE it does not work

---

### Post by TravisNewman on 2005-06-04
Well, now, when I search for "something" I get:
The query for *something* failed with error:
System.Net.Sockets.SocketException: System call failed in [0x00063] System.Net.Sockets.Socket:Connect (System.Net.EndPoint remote_end) in <0x00021> Beagle.Util.UnixClient:Connect (Mono.Posix.UnixEndPoint remoteEndPoint) in <0x00036> Beagle.Util.UnixClient:Connect (System.String path) in <0x00020> Beagle.Util.UnixClient:.ctor (System.String path) in <0x00028> Beagle.Client:SendRequest (Beagle.RequestMessage request) in <0x00010> Beagle.Client:SendAsync (Beagle.RequestMessage request) in <0x000c7> Beagle.RequestMessage:SendAsync () in <0x00142> Best.BestWindow:Search (System.String searchString)

I'll be glad when this gets easier ;)

---

### Post by jdong on 2005-06-04
Open up a terminal and run **beagled**

---

### Post by TravisNewman on 2005-06-04
I knew that much. It didn't help ;)

---

### Post by skabber on 2005-06-04
after the update to beagle 0.0.10 running beagled gives this

Unhandled Exception: System.ArgumentOutOfRangeException: < 0
Parameter name: length
in [0x00088] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System/String.cs:229) System.String:Substring (Int32 startIndex, Int32 length)
in <0x00167> Beagle.Util.Logger:PruneOldLogs (System.String path, System.String instance)
in <0x00123> Beagle.Util.Logger:LogToFile (System.String path, System.String name, Boolean foreground_mode)
in <0x002f9> Beagle.Daemon.BeagleDaemon:Main (System.String[] args)
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.

---

### Post by bk452 on 2005-06-04
[QUOTE=jdong]Also, make sure your root/home filesystems are mounted with Extended Attributes (mount option xattr)[/QUOTE]
 Also, make sure your root/home filesystems are mounted with Extended Attributes (mount option xattr)***

How do you do this?

---

### Post by skabber on 2005-06-05
[QUOTE=bk452]Also, make sure your root/home filesystems are mounted with Extended Attributes (mount option xattr)***

How do you do this?[/QUOTE]

add it to the options in your /etc/fstab like so
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdb1       /               ext3    defaults,errors=remount-ro,user_xattr 0       1

---

### Post by bugmenot on 2005-06-18
[QUOTE=panickedthumb]Well, now, when I search for "something" I get:
The query for *something* failed with error:[/QUOTE]
I have the exact same problem..

---

### Post by bugmenot on 2005-06-18
[QUOTE=infinito]Everyone trying to get Beagle to work on Ubuntu Hoary should read this Howto I wrote:
[http://infinito.f2o.org/blog/?p=28](http://infinito.f2o.org/blog/?p=28)

Lot of people from this forum (and others) tried it succesfully.[/QUOTE]

I followed it exactly, but still have this error when searching for *something*:

De zoekopdracht naar *something* is mislukt met fout:
System.Net.Sockets.SocketException: System call failed in [0x00063] System.Net.Sockets.Socket:Connect (System.Net.EndPoint remote_end) in <0x00021> Beagle.Util.UnixClient:Connect (Mono.Posix.UnixEndPoint remoteEndPoint) in <0x00036> Beagle.Util.UnixClient:Connect (System.String path) in <0x00020> Beagle.Util.UnixClient:.ctor (System.String path) in <0x00028> Beagle.Client:SendRequest (Beagle.RequestMessage request) in <0x00010> Beagle.Client:SendAsync (Beagle.RequestMessage request) in <0x000c7> Beagle.RequestMessage:SendAsync () in <0x00142> Best.BestWindow:Search (System.String searchString)

---

### Post by hellraiser_rob on 2005-07-04
yup i have this issue aswell

---

### Post by hellraiser_rob on 2005-07-04
whoops hold on, it maybe because its not done indexing...?

try beagle-index-info

and beagle-status

from a standard user terminal, and see what results you get

---

