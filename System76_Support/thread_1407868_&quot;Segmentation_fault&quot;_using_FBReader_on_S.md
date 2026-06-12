---
title: "&quot;Segmentation fault&quot; using FBReader on Starling"
date: 2010-02-15
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-02-15
Today I downloaded two e-books from Project Gutenberg in the epub format to a folder I created in my Home directory.

After downloading the first one, I opened the FBReader application and added the first of the e-books to the library. I scrolled through the book from within the FBReader application and it appeared to be displaying fine. No problems. I closed the FBReader.

I then downloaded the second e-book. I went to open the FBReader application and it would not open. Or, more accurately, it appeared as if it would open for a split second but immediately close.

I went to Synaptic and reinstalled FBReader and two other associated programs (ZLibrary Core). I rebooted the Starling. I still had the same problem: I could not open FBReader.

I went to the Terminal Window and typed 'fbreader' on the command line (without the quote marks) and the response I got was:

segmentation fault

I am somewhat of a Linux newbie. Can someone please tell me what my problem is and how to fix it?

Thanks!

---

### Post by ShowMeGrrl on 2010-02-15
Don't know if it is of any relevance at all but before downloading the e-books or opening FBReader, I did the update suggested by Update Manager, which was a security fix involving flash plugin (as I recall).

---

### Post by abry on 2010-02-16
It stoped working for me as well. To workaround this problem I used FBreader repository here: [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/) and then I installed "libzlui-qt4". The program now can be started by "FBReader -zlui qt4"

Segmentation fault does still exist with gtk with version in repository.

---

### Post by ShowMeGrrl on 2010-02-16
I think your diagnosis of the problem is correct, but the solution is not working for me. 

I think your diagnosis is correct, because here is what the FBReader/desktop page says:

> "Latest stable version of FBReader is 0.12.2. FBReader package is included into popular linux distributions (Ubuntu, Debian, Fedora, Mandriva, AltLinux, etc.). However in most cases package version is obsolete. From this site you can download
Newest packages for Debian/Ubuntu distributions (for both i386 and amd64 platforms), or
Source tarball."

However, unfortunately, though I followed the directions for installing the updated fbreader package from the FBReader repository, I got an error message during the installation:

"E: /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb: trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9"
 
Basically, the Starling refuses to download one of the files (or packages) in the installation package (libzltext) because it tries to overwrite another libz file already on the Starling. Without that file, I get a "broken package" message and am told to fix it using Synaptic. I can "fix" the broken package but the libzltext file still isn't loaded onto the Starling and I can't get the otherwise updated FBReader (I have a new desktop icon) to open. 

When I type "FBReader -zlui qt4" in the command line (without the quotes), I get this message in response:

"FBReader: error while loading shared libraries: libzltext.so.0.13: cannot open shared object file: No such file or directory"

I am not even allowed to uninstall the FBReader, because when I mark it for removal, the frightening message Synaptic gives me is that I am asking to uninstall Ubuntu Netbook Remix!

I'm a little frustrated at this point. Suggestions most welcome.

---

### Post by thomasaaron on 2010-02-16
I loaded FBReader, went to Project Gutenberg, downloaded a book and it started fine.

I then went installed updates (which included that Flash update) and restarted FBReader. No issues.

So, I'm unable to reproduce it.

It sounds, though, like you now have a nasty package dependency problem in which you can't uninstall FBReader without removing a library that UNR depends on for other things.

Try running...

sudo apt-get install -f

...to see if it can resolve the dependency issue on its own.

---

### Post by ShowMeGrrl on 2010-02-16
Thomas, I should have mentioned that when I downloaded the e-books from Project Gutenberg, I downloaded the epub versions. Something I read online (unfortunately later) mentioned that FBReader's epub support is "incomplete" or something like that. When I opened the epub file, it seemed to display fine. However, once I closed the FBReader program, things when downhill and I could never reopen FBReader after that. So my guess at this point is that FBReader could not handle the epub file.

Second, I did as you suggested (apt-get install -f). Initially it looked promising but then I got a similar error message to what I got before (see below) and I appear to be back where I was with this persistent "broken package" message. I "fix" it in Synaptic, but then it comes right back next time I boot up.

> Unpacking libzltext (from .../libzltext_0.12.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)		


I tried uninstalling the libzltext0.9 file/package and planned to replace it with the libzltext file/package, thinking that might eliminate the conflict, since there would be nothing to overwrite.  But Synaptic insists on installing the new file before uninstalling the libzltext0.9, so I get the same old error message. And maybe it wasn't a good idea I had anyway. Maybe it was even dangerous. I'm too naive to know.

---

### Post by thomasaaron on 2010-02-16
I downloaded an epub and didn't have any issues. While I can see the epub file crashing FBReader, it shouldn't break anything else (permanently).

So, please clarify... Where did you download libzlui-qt4 from? The repositories? Or from another source? And, did it seem to install properly?

Also, please open Synaptic and search for "libzltext". Take a screensot of what is installed and attach it.

We need to remove one of the packages, but I'm not sure which one yet.

Are you running 9.04?

---

### Post by ShowMeGrrl on 2010-02-16
Thanks for your time on this, Thomas.

1. > So, please clarify... Where did you download libzlui-qt4 from? The repositories? Or from another source? And, did it seem to install properly?

I followed exactly the suggestions of abry above to download from the FBReader repository. If you go to [http://fbreader.org/desktop/](http://fbreader.org/desktop/) you will see this section on that page:

> Installation from the repository:
add the following lines to your /etc/apt/sources.list: 
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main 
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main
(optional) install our PGP key:
download the key file
as root, run ‘apt-key add geometer.fbreader.org.asc’
as root, run ‘apt-get update’.
(optional) by default, gtk+ interface module will be installed. If you prefer to use FBReader with qt (or with qt4) inreface, run with root privileges ‘apt-get install libzlui-qt’ (or ‘apt-get install libzlui-qt4’).
as root, run ‘apt-get install fbreader’. 

I followed these instructions pretty carefully except the optional "install our PGP key:" and also I don't remember if I downloaded the key file. I did get some kind of notice about the PGP or key as I was installing, as I recall. I think it was to the effect  that the downloads were unauthenticated because of a key issue. But I just plowed ahead.

Other than the key problem and the error message about libzltext trying to overwrite hyphenationPatterns.zip in libzltext09 ("E: /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb: trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9") everything seemed to install OK. And, as I mentioned, I then had a new FBReader icon on my UNR desktop in place of the old icon.

I agree with you that an epub file that crashes FBReader shouldn't foul things up so badly and permanently, but remember that the problem I had of being unable to open FBReader happened BEFORE I did any of this downloading of libzltext, libzlui-qt4 or  any other FBReader packages. 

Before I went to abry's suggestions, I tried rebooting and then reinstalling FBReader through Synaptic and rebooting and that did not solve the problem with the FBReader program. 

2. > Also, please open Synaptic and search for "libzltext". Take a screensot of what is installed and attach it.

I have attached the screenshot. It shows that libzltext0.9 is installed and that libzltext-dev is not installed. 

I tried to fix the broken package in Synaptic by filtering for broken dependencies, which brought up the fbreader package, and then clicking on "fix broken packages." That produced the message in the status bar at the bottom that the broken dependencies were successfully fixed. 

However, as soon as I try to close down Synaptic, I get the message that "There are still marked changes that have not yet been applied. They will get lost if you choose to quit Synaptic."  If I "apply" the "marked changes," I get the error message about libzltext trying to overwrite the other file. If I quit without applying the marked changes, I get a message telling me I have a broken package. And when I open Update Manager, there is the libzltext file waiting to be installed. If I install it, I get the error message about libzltext trying to overwrite. In other words, all paths lead to the same bad place: broken package and inoperative fbreader and inability to uninstall fbreader.


3.>  Are you running 9.04?

Yes. I am running 9.04.

---

### Post by thomasaaron on 2010-02-17
OK, thanks.

Well, that tutorial definitely jams the heck out of synaptic package manager. I've been able to duplicate the problem on my own system, and fix it, but it was a bit roundabout, so this may take a few more volleys.

First, go to System > Administration > Software Sources and make sure the two repositories listed in the instructions are indeed added and activated. Then click the Reload button.

Now, go to Synaptic Package Manager and search for and delete each of these packages ***one at a time,*** making sure with each one you're not obliterating UNR.

libzltext
libzlcore
libzlui-gtk
libzlui-qt4
fbreader

If there are any issues along the way, let me know. If all of that seemed to be successful, then go back to software sources and ***deactivate*** those two repositories and click Reload again.

Then go back to Synaptic Package Manager and search for / install fbreader.

Did that work?

---

### Post by ShowMeGrrl on 2010-02-17
Thanks, Thomas. Here is a question I have about your instructions. You tell me to delete libzltext, but Synaptic shows that I don't have libzltext installed. Rather, I have libzltext0.9
installed. Are you telling me they are the same thing or, at least, that I should delete libzltext0.9?

Similarly, you tell me to delete libzlcore, but Synaptic does not show that package. Instead, Synaptic shows that I have 
libzlcore0.9
libzlcore-data

installed. Should I delete neither of these, one of these, both of these?

---

### Post by thomasaaron on 2010-02-17
I know what you're saying. I saw the same thing on my system. If the package I mentioned above isn't installed, just move to the next package. Those... variants should just be left alone for now.

---

### Post by ShowMeGrrl on 2010-02-17
No luck, unfortunately.

libzltext   -- not installed on my system
libzlcore   -- not installed on my system
libzlui-gtk  -- to delete this is to delete Ubuntu Netbook Remix
libzlui-qt4  -- to delete this is to delete both UNR & FBReader
fbreader     -- to delete this is to delete UNR

What do you suggest?

---

### Post by thomasaaron on 2010-02-18
Heck if I know! :popcorn:

Let's try this...

sudo rm /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Then try the instructions above again.

PS: It's time to start making sure you're well backed up.

---

### Post by ShowMeGrrl on 2010-02-19
Thanks, Thomas. I can't do these instructions right now but will do it as soon as I am able and report back.
 
:)

---

### Post by ShowMeGrrl on 2010-02-22
OK, I was able to do these latest suggestions. Attached is a copy of the terminal dialogue for all of these commands.

Note that amongst all of the verbiage here is the same old error message regarding libzltext trying to overwrite "hyphenationPatterns.zip"

> Unpacking libzltext (from .../libzltext_0.12.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1):After doing your suggested terminal commands, I tried repeating the earlier instructions.
Results were similar with slight differences. Before, libzlcore was not installed on my system. This time it's installed but when I try to delete it, I am informed I will be deleting Ubuntu Netbook Remix if I delete it. Before, when I tried to delte libzlui-gtk, I was told I would be delting UNR. This time I am told I will be deleting both FBReader and UNR. 

libzltext   -- not installed on my system
libzlcore   -- to delete this is to delete Ubuntu Netbook Remix
libzlui-gtk  -- to delete this is to delete FBReader & Ubuntu Netbook Remix
libzlui-qt4  -- to delete this is to delete both UNR & FBReader
fbreader     -- to delete this is to delete UNR

Currently, I am still unable to open the FBReader program. I still am receiving notifications that I have a broken package (FBReader). And, strangely, my Documents folder just disappeared from the right-hand Places panel on the Desktop. I can still get to it by going through the Home folder, but that's kind of an extra step for getting to a folder that I use a lot. Don't know if it is related to any of this, although it did disappear while I was doing all this stuff.

:(

Suggestions desired!

---

### Post by ShowMeGrrl on 2010-02-22
For whatever reason, I was unable to attach that terminal dialogue that I mentioned in the previous message, so I'll just do it inline here:

> jhadle@system76-netbook:~$ sudo rm /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
[sudo] password for jhadle: 
rm: cannot remove `/var/cache/apt/archives/libzltext_0.12.2-1_i386.deb': No such file or directory
jhadle@system76-netbook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 libxine1-misc-plugins libxcb-xv0 libxine1-bin libexiv2-5 librasqal1 libsoprano4
  redland-utils libxcb-shape0 linux-backports-modules-2.6.28-11-generic exiv2 libxcb-shm0 soprano-daemon libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libzltext
The following NEW packages will be installed:
  libzltext
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 395kB of archives.
After this operation, 623kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libzltext
Install these packages without verification [y/N]? y
Get:1 [http://www.fbreader.org](http://www.fbreader.org) stable/main libzltext 0.12.2-1 [395kB]
Fetched 395kB in 1s (235kB/s)     
(Reading database ... 243251 files and directories currently installed.)
Unpacking libzltext (from .../libzltext_0.12.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jhadle@system76-netbook:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of fbreader:
 fbreader depends on libzltext (>= 0.12.2-1); however:
  Package libzltext is not installed.
 fbreader depends on libzltext (<< 0.13.0); however:
  Package libzltext is not installed.
dpkg: error processing fbreader (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fbreader
jhadle@system76-netbook:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US                                                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                                                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]                                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                                                                  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [223kB]                                                     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2612B]                                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [63.1kB]                                                     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [617B]                                                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [108kB]                                                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [30.0kB]                                                 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8561B]                                              
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2911B]                                               
Hit [http://planet76.com](http://planet76.com) ./ Release.gpg                                                                                      
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US                                                                                
Hit [http://planet76.com](http://planet76.com) ./ Release                                                                                          
Ign [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Get:12 [http://www.fbreader.org](http://www.fbreader.org) stable Release.gpg [189B]                                                                    
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Translation-en_US                                                                   
Hit [http://planet76.com](http://planet76.com) ./ Packages                                                                                         
Get:13 [http://www.fbreader.org](http://www.fbreader.org) stable Release [984B]                                                                        
Ign [http://www.fbreader.org](http://www.fbreader.org) stable Release                                                                                  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                            
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Packages                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]                         
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                           
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main Packages                           
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                                                                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                                                                   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [135kB]                                                     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2612B]                                               
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [36.8kB]                                                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [617B]                                                 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [78.2kB]                                                
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [19.9kB]                                                 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [1669B]                                               
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [580B]                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Get:24 [http://dl.google.com](http://dl.google.com) stable Release [2540B]
Get:25 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1010B]
Get:26 [http://dl.google.com](http://dl.google.com) stable/main Packages [868B]
Fetched 835kB in 2min 0s (6903B/s)
Reading package lists... Done
W: GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101
W: You may want to run apt-get update to correct these problems
jhadle@system76-netbook:~$ 
jhadle@system76-netbook:~$ sudo apt-get --assume-yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  fbreader: Depends: libzltext (>= 0.12.2-1) but it is not installed
            Depends: libzltext (< 0.13.0) but it is not installed
E: Unmet dependencies. Try using -f.
jhadle@system76-netbook:~$ 



---

### Post by ShowMeGrrl on 2010-02-22
Ignore my complaint about the Documents folder disappearing from the Places panel.  I have fixed that.

---

### Post by thomasaaron on 2010-02-22
Open Synaptic Package Manager and search for libzltext. Can you see a version >= 0.12.2-1.

If you can, install it. Then try the above instructions again.

---

### Post by ShowMeGrrl on 2010-02-22
> Open Synaptic Package Manager and search for libzltext. Can you see a version >= 0.12.2-1.

If you can, install it. Then try the above instructions again. 	


Yes, I can see that version of that package but when I try to install it, I get the same old error message:

"E: /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb: trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9"

---

### Post by thomasaaron on 2010-02-23
OK, run...

sudo mv /usr/share/zlibrary/hyphenationPatterns.zip /usr/share/zlibrary/hyphenationPatterns.zip.bk

...and then try again.

---

### Post by ShowMeGrrl on 2010-02-26
> **thomasaaron said:**
> OK, run...

sudo mv /usr/share/zlibrary/hyphenationPatterns.zip /usr/share/zlibrary/hyphenationPatterns.zip.bk



OK, I have done this. However, now I am not certain when you then say "...and then try again." whether you mean that I should now try these instructions again:

> 
sudo rm /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade



or whether you mean I should now try these instructions again:

> 

First, go to System > Administration > Software Sources and make sure the two repositories listed in the instructions are indeed added and activated. Then click the Reload button.

Now, go to Synaptic Package Manager and search for and delete each of these packages ***one at a time,*** making sure with each one you're not obliterating UNR.

libzltext
libzlcore
libzlui-gtk
libzlui-qt4
fbreader

If there are any issues along the way, let me know. If all of that seemed to be successful, then go back to software sources and ***deactivate*** those two repositories and click Reload again.

Then go back to Synaptic Package Manager and search for / install fbreader.



or whether I should do both sets of instructions. And, if both, in which order. Perhaps the answer is obvious to most people, but, sorry, it's not obvious to me and I want to make sure I do it correctly.

---

### Post by thomasaaron on 2010-02-26
I'm sorry. I meant follow these instructions again...
> 
Open Synaptic Package Manager and search for libzltext. Can you see a version >= 0.12.2-1.

If you can, install it. Then try the above instructions again. 

---

### Post by ShowMeGrrl on 2010-02-26
> **thomasaaron said:**
> I'm sorry. I meant follow these instructions again...

OK, I tried this and got this same old error message:

>   E: /var/cache/apt/archives/libzltext_0.12.2-1_i386.deb: trying to overwrite `/usr/share/zlibrary/hyphenationPatterns.zip', which is also in package libzltext0.9 

I went back and re-did the prior instruction ("sudo mv /usr/share/zlibrary/hyphenationPatterns.zip /usr/share/zlibrary/hyphenationPatterns.zip.bk") just to make sure that that zip file had been renamed. When I typed in the mv command, the terminal responded: >  mv: cannot stat `/usr/share/zlibrary/hyphenationPatterns.zip': No such file or directory 

Also, when I first tried to install that libzltext version >= 0.12.2-1, besides getting the error message mentioned above, I also got notice of a "crash report," though I don't know what crashed. I had only two programs (Firefox and Synaptic) open at the time (that I am aware of) and both continued to function properly. The second time I tried to install the libzltext file (in order to copy the error message), I got no crash report.

I can't understand why I'm getting the overwrite error message when that file that's supposedly being overwritten doesn't exist.

---

### Post by ShowMeGrrl on 2010-02-26
I've done a search and the hyphenationPatterns.zip file is not on my Starling. I rebooted and tried again to install the libzltext file and got the same error message.

I'm wondering if Synaptic rather than checking the harddrive for the actual hyphenationPatterns.zip file instead has an index of the files in the libzltext0.9 package and **assumes** that all the files in that index are on the computer, whether or not they actually are. Where this leaves us, I'm not sure.

---

### Post by ShowMeGrrl on 2010-02-26
Hey! Hallelujah! My problem seems to be fixed, though I'm not sure why or how. 

I realized the Update Manager hadn't been run in a while, so I opened it and saw that there were some Firefox updates. Also, there was the problematic libzltext file there waiting to be installed. That's the file that always throws up the error message about overwriting the hyphenationPatterns.zip file. I unchecked it hoping that the Update Manager would install only the Firefox updates and not the libzltext. It did as I hoped. 

Slowly, I realized that I had not received the usual message of a "broken package" when closing the Synaptic Manager. And I noticed the "broken package" icon was gone from the panel at the top of the desktop. I opened the "Office" section of the Applications panel and saw that the FBReader icon was gone! 

So it appears that I'm in business again -- no broken packages and FBReader uninstalled.

Now I just need to find a good e-book reader program, but that is a different topic -- one I'll be posting shortly.

Thanks, Thomas!

---

### Post by thomasaaron on 2010-03-01
Whew. Thank goodness for small blessings!

---

