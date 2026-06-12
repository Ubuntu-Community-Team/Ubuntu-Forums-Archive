---
title: "installing OpenSim"
date: 2008-11-26
forum: Server Platforms
---

### Post by Tohasu on 2008-11-26
I have a VPSLink server account and am running Ubuntu 8.04 as the OS.  I am trying to install OpenSim which is the open source Second Life software.  Yes, I want to have my own world...

I'm an experienced user but a noob to unix/linux systems.  So far I think I've manage to apt-get some utilities I need, like subversion, aptitude, and mono, and I have the opensim code downloaded too.  Here's a snapshot of the install process.
=====================================
2. Install on Ubuntu 8.04/8.10 (from OpenSim.org web site [http://opensimulator.org/wiki/Build_Instructions](http://opensimulator.org/wiki/Build_Instructions))
Recent versions of OpenSim come without an OpenSim.ini file. Copy the OpenSim.ini.example file to OpenSim.ini before making any changes.

sudo apt-get install subversion nant mono-gmcs mono-dbg \libmono-system-runtime2.0-cil libgdiplus libmono-i18n2.0-cil ruby

svn co [http://opensimulator.org/svn/opensim/trunk](http://opensimulator.org/svn/opensim/trunk) opensim

cd opensim

./runprebuild.sh

nant


3. Running Open Sim

Note: if you are running a 32bit Server such as Ubuntu 8.0.4 you need the alternative launcher:
cd bin
mono OpenSim.32BitLaunch.exe
====================

I think I managed to get most of this done.  It's hard to tell because my terminal keeps locking up.  So I run something like nant and get BUILD SUCCESSFUL and a locked terminal.

When I try to do the launch in the last step I get the following.  My best guess is that a path has not been properly created, maybe in the earlier prebuild script step.

Anyway, I'm fairly stumped for now and any comments or help would be much appreciated.

Thanks in advance.

Tohasu/Tom

=======================

root@tohasumoore:~/opensim/bin# mono OpenSim.32BitLaunch.exe

** (OpenSim.32BitLaunch.exe:26578): WARNING **: The following assembly referenced
from /root/opensim/bin/OpenSim.32BitLaunch.exe could not be loaded:
     Assembly:   OpenSim    (assemblyref_index=2)
     Version:    0.0.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO
_PATH environment variable, or in the location of the executing assembly (/root/op
ensim/bin/).


** (OpenSim.32BitLaunch.exe:26578): WARNING **: Could not load file or assembly 'O
penSim, Version=0.0.0.0, Culture=neutral' or one of its dependencies.

** (OpenSim.32BitLaunch.exe:26578): WARNING **: Missing method Main in assembly /r
oot/opensim/bin/OpenSim.32BitLaunch.exe, type OpenSim.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assem
bly 'OpenSim, Version=0.0.0.0, Culture=neutral' or one of its dependencies.
File name: 'OpenSim, Version=0.0.0.0, Culture=neutral'
root@tohasumoore:~/opensim/bin#
======================

---

### Post by Tohasu on 2008-11-26
Having solved my terminal problems by using the Mac OS X terminal to connect to my server account... I find that nant results in a failed build.  Here are the conditions.

The instructions on the web site for Ubuntu install include this line

sudo apt-get install subversion nant mono-gmcs libmono-microsoft8.0-cil \
     libmono-system-runtime2.0-cil libgdiplus libmono-i18n2.0-cil ruby

BUT 

 libmono-microsoft8.0-cil

is not available and has been replaced by mono-dbg, so I revised the apt-get to read

sudo apt-get install subversion nant mono-gmcs mono-dbg \
     libmono-system-runtime2.0-cil libgdiplus libmono-i18n2.0-cil ruby


Now my build fails with this message

 build:
            
                 [echo] Build Directory is /root/opensim/OpenSim/Region/ScriptEngine/Shared/CodeTools/bin/Debug
                [mkdir] Creating directory '/root/opensim/OpenSim/Region/ScriptEngine/Shared/CodeTools/bin/Debug'.
                  [csc] Compiling 8 files to '/root/opensim/OpenSim/Region/ScriptEngine/Shared/CodeTools/bin/Debug/OpenSim.Region.ScriptEngine.Shared.CodeTools.dll'.
                  [csc] /root/opensim/OpenSim/Region/ScriptEngine/Shared/CodeTools/Compiler.cs(34,17): error CS0234: The type or namespace name `JScript' does not exist in the namespace `Microsoft'. Are you missing an assembly reference?
                  [csc] Compilation failed: 1 error(s), 0 warnings
            
            BUILD FAILED - 0 non-fatal error(s), 1 warning(s)
            
            /root/opensim/OpenSim/Region/ScriptEngine/Shared/CodeTools/OpenSim.Region.ScriptEngine.Shared.CodeTools.dll.build(14,10):
            External Program Failed: /usr/lib/mono/2.0/gmcs.exe (return code was 1)
            
            Total time: 1.2 seconds.
            

BUILD FAILED

Nested build failed.  Refer to build log for exact reason.

Total time: 77.8 seconds.

Is the failure due to the change to mono-dbg?  If so, what has to be patched to fix it?  Does the prebuild have to be modified?  Where is the build log kept?  

Any help much appreciated.  I think I'm close to getting OpenSim to run on a Ubuntu server.

Thanks.

Tom

---

### Post by directhex on 2008-11-26
No, that's not right, libmono-microsoft8.0-cil is definitely the package you want for Microsoft.JScript.dll

Why would a "real" library be in a debug symbols package like mono-dbg?

---

### Post by Tohasu on 2008-11-26
> **directhex said:**
> No, that's not right, libmono-microsoft8.0-cil is definitely the package you want for Microsoft.JScript.dll

Why would a "real" library be in a debug symbols package like mono-dbg?

=========
I'll have another run at getting thelibmono-microsoft8.0-cil.  As for your comment about a "real library" -- I'm afraid I'm too much of a noob to know, but I'm getting the idea the the mono-dbg package is inadequate.  thanks.

---

### Post by ilayda on 2009-03-27
I want to install opensim in ubuntu 8.04 LTS 64bit , it is a VPS and I am a complete linux dummy girl. I found some instructions such as above, but non is matching, some is not for 64bit, others are referin older versions of sofwares which are not avaible etc.. So I failed to install several times. Can someone help me ?

---

### Post by directhex on 2009-03-27
> **ilayda said:**
> I want to install opensim in ubuntu 8.04 LTS 64bit , it is a VPS and I am a complete linux dummy girl. I found some instructions such as above, but non is matching, some is not for 64bit, others are referin older versions of sofwares which are not avaible etc.. So I failed to install several times. Can someone help me ?

Step 1: Add my Hardy backports repo for Mono. Hardy's Mono is ancient. See [http://directhex.mfgames.com/](http://directhex.mfgames.com/)

Step 2: Install the following packages: subversion nant libmono-system-runtime2.0-cil libmono-microsoft8.0-cil

Step 3: "svn co [http://opensimulator.org/svn/opensim/trunk](http://opensimulator.org/svn/opensim/trunk) opensim"

Step 4: "cd opensim"

Step 5: "nant"

Step 6: "cd bin"

Step 7: "mono OpenSim.exe"

Result:
```
root@osc-franzibald:/tmp/opensim/bin# lsb_release -sd
Ubuntu 8.04.2
root@osc-franzibald:/tmp/opensim/bin# mono OpenSim.exe
log4net:ERROR XmlHierarchyConfigurator: No appender named [NHibernateFileLog] could be found.
log4net:ERROR XmlHierarchyConfigurator: Appender named [NHibernateFileLog] not found.
08:46:41 - Performing compatibility checks... 
08:46:41 - Environment is compatible.
```

From there, it's your call to actually configure the thing

---

### Post by ilayda on 2009-03-27
thanks a lot directhex, I will try it as soon as I figure out how can I add your backports repo from the console , any suggestion please ?

---

### Post by directhex on 2009-03-27
> **ilayda said:**
> thanks a lot directhex, I will try it as soon as I figure out how can I add your backports repo from the console , any suggestion please ?

Add the repo line to /etc/apt/sources.list.d/directhex.list

For the GPG key, download the .asc and use "apt-key add directhex.asc"

---

### Post by ilayda on 2009-03-29
Aww, thanks alot , you rock!  it works , up and running now , just I am having some errors with J2KDecoderModule

---

### Post by NZ-Wanderer on 2009-04-28
Quick question if I may, Can I use this with the new 9.04 release?? - I asking instead of trying it because I really don't want to reformat my server machine and only then find out it wouldn't work :P

> **directhex said:**
> Step 1: Add my Hardy backports repo for Mono. Hardy's Mono is ancient. See [http://directhex.mfgames.com/](http://directhex.mfgames.com/)
Step 2: Install the following packages: subversion nant libmono-system-runtime2.0-cil libmono-microsoft8.0-cil
Step 3: "svn co [http://opensimulator.org/svn/opensim/trunk](http://opensimulator.org/svn/opensim/trunk) opensim"
Step 4: "cd opensim"
Step 5: "nant"
Step 6: "cd bin"
Step 7: "mono OpenSim.exe"
Result:
```
root@osc-franzibald:/tmp/opensim/bin# lsb_release -sd
Ubuntu 8.04.2
root@osc-franzibald:/tmp/opensim/bin# mono OpenSim.exe
log4net:ERROR XmlHierarchyConfigurator: No appender named [NHibernateFileLog] could be found.
log4net:ERROR XmlHierarchyConfigurator: Appender named [NHibernateFileLog] not found.
08:46:41 - Performing compatibility checks... 
08:46:41 - Environment is compatible.
```
From there, it's your call to actually configure the thing

---

### Post by directhex on 2009-04-29
> **NZ-Wanderer said:**
> Quick question if I may, Can I use this with the new 9.04 release?? - I asking instead of trying it because I really don't want to reformat my server machine and only then find out it wouldn't work :P

Yep, sure. Jaunty has even newer Mono than my Hardy backports, so just jump straight to the installing-packages-and-compiling-opensim part

---

### Post by NZ-Wanderer on 2009-04-29
> **directhex said:**
> Yep, sure. Jaunty has even newer Mono than my Hardy backports, so just jump straight to the installing-packages-and-compiling-opensim part

Thanks for that :) - soon as I find out if there is a mysql for linux (which I presuming there is) I will go ahead and install Ubuntu on my server machine...

I am presuming I use synaptic to install the packages before compiling the opensim part, and would also have the linux mysql installed before compiling as well? :)

I been running opensim in grid mode and have 4 islands working, but would rather do it under ubuntu server or normal ubuntu cause it's not as resourse hungry as windows is :P

hmm that reminds me I better OAR all my islands before I do this otherwise I will lose the lot :P

---

### Post by directhex on 2009-04-29
> **NZ-Wanderer said:**
> Thanks for that :) - soon as I find out if there is a mysql for linux (which I presuming there is) I will go ahead and install Ubuntu on my server machine...

There's a MySQL for **NOT** Linux? :o

> I am presuming I use synaptic to install the packages before compiling the opensim part, and would also have the linux mysql installed before compiling as well? :)

Nope, doesn't need MySQL installed to compile. Really, just the list of packages I gave already.

---

### Post by NZ-Wanderer on 2009-04-29
> **directhex said:**
> There's a MySQL for **NOT** Linux? :o
Nope, doesn't need MySQL installed to compile. Really, just the list of packages I gave already.

Thanks, am just downloading the Ubuntu Server package now,then I will repartition one of my drives ready and see what happens :P:P

---

### Post by NZ-Wanderer on 2009-04-30
> **directhex said:**
> Step 3: "svn co [http://opensimulator.org/svn/opensim/trunk](http://opensimulator.org/svn/opensim/trunk) opensim"
Step 4: "cd opensim"
Step 5: "nant"


One thing I found today, between step 4 and step 5 you have to issue the command ./runprebuild.sh

ok, now to see if this thing works and then install mysql :)

---

### Post by Markor on 2009-05-13
Can we have/make *.deb 64/32 bit package for it?
(Hardy, Jaunty, Interpid)
I would prefer to install from package instead directly without it,
so that I can remove or upgrade it at later time..
10x ;)

---

### Post by directhex on 2009-05-13
> **Markor said:**
> Can we have/make *.deb 64/32 bit package for it?
(Hardy, Jaunty, Interpid)
I would prefer to install from package instead directly without it,
so that I can remove or upgrade it at later time..
10x ;)

The license seems free at first glance, so you can do it yourself - and Mono apps are cross-platform so no need for 32/64 split

---

### Post by directhex on 2009-05-13
> **directhex said:**
> The license seems free at first glance, so you can do it yourself - and Mono apps are cross-platform so no need for 32/64 split

Erm, maybe not - 25 different third party libs with their own licenses. This is a packager's nightmare

---

### Post by outofnicks on 2009-09-06
Maybe I should start a fresh thread, but this is on topic so I'll give it a shot first.

I have been running Opensim using OSGrid's binary prebuilds but now want to try the cutting edge. I have upgraded Mono to 2.4.2 using this tutorial:
[http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)

And I believe I have all other dependancies taken care of for compiling-since I was able to build a recent version of Mono.

Think all I need now is nant, but when I use apt-get or Synaptic to install, it wants to install an older version of Mono.

Will that overwrite my custom build of 2.4.2, or not? Is there an alternative way to install Nant without affecting my current Mono install?

---

### Post by directhex on 2009-09-07
> **outofnicks said:**
> Maybe I should start a fresh thread, but this is on topic so I'll give it a shot first.

I have been running Opensim using OSGrid's binary prebuilds but now want to try the cutting edge. I have upgraded Mono to 2.4.2 using this tutorial:
[http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://blog.ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)

And I believe I have all other dependancies taken care of for compiling-since I was able to build a recent version of Mono.

Think all I need now is nant, but when I use apt-get or Synaptic to install, it wants to install an older version of Mono.

Will that overwrite my custom build of 2.4.2, or not? Is there an alternative way to install Nant without affecting my current Mono install?

The guide you followed is INCREDIBLY harmful, and I'm finding myself needing to try and fix that mess for people about once a week at the moment

---

### Post by outofnicks on 2009-09-07
> The guide you followed is INCREDIBLY harmful, and I'm finding myself needing to try and fix that mess for people about once a week at the moment

Thanks for replying. 
Can you tell me why this is so, and where the best place is to put Mono please? 

The current versions of OpenSim call for version 2.4 and I think a few people have followed that tutorial. I've recommended it a couple times, and certainly don't want to do that anymore if it's harmful. I did a bunch of googling, and the only other location I saw was /opt.

With one exception, in /home/user/bin  which was recommended by the leaders of OSGrid, the most popular grid for OpenSim. Makes sense, doesn't it? If you're gonna bork something, just bork the userspace. 
Good idea you think, or not?

Thanks again!

---

### Post by directhex on 2009-09-07
> **outofnicks said:**
> Thanks for replying. 
Can you tell me why this is so, and where the best place is to put Mono please? 

The current versions of OpenSim call for version 2.4 and I think a few people have followed that tutorial. I've recommended it a couple times, and certainly don't want to do that anymore if it's harmful. I did a bunch of googling, and the only other location I saw was /opt.

With one exception, in /home/user/bin  which was recommended by the leaders of OSGrid, the most popular grid for OpenSim. Makes sense, doesn't it? If you're gonna bork something, just bork the userspace. 
Good idea you think, or not?

Thanks again!

[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

Which is linked to from mono-project.com's download section. Not that I have write access to mono-project.com or anything. *cough*

The reason it's harmful is that Mono has a centralised list of system-wide libraries, called the "Global Assembly Cache" - and when you install yourself such that there's a new "mono" in a bin folder in $PATH, then when a user runs "fooapp", it runs with your self-made mono for preference, not the copy in /usr/bin - which means that if the app needs a library which is in the system GAC in /usr/lib/mono/gac and not the GAC which is actually being used here (the copy in /usr/local/lib/mono/gac) then it'll fail to run with annoying and unhelpful errors about libraries not being found

---

### Post by afrodeity on 2009-12-06
I have just installed the binary from the [unofficial Ubuntu opensim repo.]("http://opensimulator.org/wiki/UnofficialDebPackages") Obviously need to make a symbolic link, but not sure how to do this for a directory.
This is the error

```
frodeity@afrodeity-desktop:/usr/lib/opensim/bin$ mono ./opensim.exe
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory.
afrodeity@afrodeity-desktop:/usr/lib/opensim/bin$ locate mscorlib.dll
/usr/lib/mono/2.0/mscorlib.dll

```

UPDATE: okay, I made a symbolic link:/usr/lib/mono/2.0/ /usr/lib/mono/1.0/

 ```
 ln -s /path/to/real/file /path/to/non-existant/file 
```

and copied OpenSim.Example.xml to OpenSim.ini

now I get this if I run OpenSim.exe 

```

log4net:ERROR XmlHierarchyConfigurator: No appender named [NHibernateFileLog] could be found.
log4net:ERROR XmlHierarchyConfigurator: Appender named [NHibernateFileLog] not found.
21:44:53 - [OPENSIM MAIN]: configured log4net using default OpenSim.exe.config
21:44:53 - Performing compatibility checks... 
21:44:54 - Environment is compatible.

21:44:54 - [CONFIG] Reading configuration settings
21:44:54 - [CONFIG] Reading configuration file /usr/lib/opensim/bin/OpenSim.ini
21:44:54 - [APPLICATION]: 
APPLICATION EXCEPTION DETECTED: System.UnhandledExceptionEventArgs

Exception: Nini.Ini.IniException: Expected assignment operator (=) - Line: 1, Position: 7.
  at Nini.Ini.IniReader.ReadKey () [0x00000] 
  at Nini.Ini.IniReader.ReadNext () [0x00000] 
  at Nini.Ini.IniReader.Read () [0x00000] 
  at Nini.Ini.IniDocument.LoadReader (Nini.Ini.IniReader reader) [0x00000] 

```

---

### Post by Rusty au Lait on 2010-06-26
Has life been getting better for you or what? Opensim install is a cake walk. Install Lucid Lynx. LAMP, and follow Opensimulator's instructions. The SQLite had problems so that's why I installed LAMP; besides, Apache will be useful, I'm sure.
Regards

---

### Post by Rusty au Lait on 2010-07-22
So. I was so young and smug back then. Two steps forward one step back.
What I described in the last reply happened once.
Right now I am starting with Lucid Lynx server with LAMP and the current opensim package from knifeiaw.com/ubuntu.
opensim is using MySQL
mono version: 2.4.4
clients: secondlife and inprudence.
The client hangs while handshaking with region when I try to login in the master avatar.
Log show no errors. I am now spending time in the osgrid's forum.
Any links would be appreciated.
tks

Still have problems with the handshaking. Where am I going wrong? opensimulator/wiki had some suggestions. Didn't help. I saw an ERROR in the log. It only said it was sending the user to the default region.
It's the journey.

---

### Post by IsaacAsimov on 2010-08-15
i have successfully installed OpenSim 0.7.0.1 (Release)  (interface version 6)
 on ubuntu server 10.04 but the IP address internally on the server (LAN address, static) is not the same as the IP address to my router (external_ip) ...so what do I do?  i cannot login with any viewer. though the opensim app appears stable. help? cheers!

---

### Post by Rusty au Lait on 2010-08-20
OK. Went back to 9.04. Works fine and I don't need MySql, SQLite works now.

Nothing new about Lucid though. I still can't install without it failing sometimes. The failure I run into the most happens during handshaking when the master avatar (or any other user) logs in.

---

### Post by trucker33377 on 2010-09-26
Hi I could use some help here, I have installed ubuntu 10.04.1 LTS
and am attempting to install opensim. when i try to start it i get an error, mscorlib.dll cannot be found or loaded...

---

### Post by directhex on 2010-09-27
> **trucker33377 said:**
> Hi I could use some help here, I have installed ubuntu 10.04.1 LTS
and am attempting to install opensim. when i try to start it i get an error, mscorlib.dll cannot be found or loaded...

Install mono-complete.

---

