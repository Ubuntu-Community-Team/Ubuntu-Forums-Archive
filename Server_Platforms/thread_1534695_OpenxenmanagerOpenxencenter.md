---
title: "Openxenmanager/Openxencenter"
date: 2010-07-19
forum: Server Platforms
---

### Post by jaime256 on 2010-07-19
I just wiped out an old installation of the enterprise xen server I had to due to the license expiration. I just don't want to deal with that while I try to test stuff and citrix doesn't make it easy to get to anything so I wanted to try out the open source **Xen Cloud Platform** since that's the only iso I found on the site in order to just install that on my test machine and not have to install another linux OS before it.

Now that that's wiped it installed fine. I downloaded openxenmanager then I found there's an openxencenter and they both look like the same thing. I'm not sure if they are or not. In any case I have ubuntu 9.04 and 10.04. Unfortunately when I try to start a vm template to get that ubuntu installed on the desktop the program just freezes no matter which one I use. I downloaded both just to check. When I try to run the program on my laptop with 10.04 it freezes the whole laptop. Also when I change the cd to and any iso or vice versa depending on what is there, the program freezes. I can connect to the server fine, I also set up a repository of the isos in a nas share using samba. I'm just using this for testing, but I'm not having any luck with this. Has anyone else had this occur or does anyone know what the problem may be. 

In order to run this program I have to go into a terminal and then to the directory. After that I have to type python window.py which then launches the program. I tried the freenode irc but although there were a few people on it I got nothing there on the openxenmanager channel I think it was and the openxencenter channel is by invitation only. I also tried the forum but still waiting to see if anyone reads that. In any case I'm sure others have tried this before me so I'm hoping I can find out a bit more on here in case anyone has used it.

If not, does anyone have any other suggestions of a better system that I could use. I already know about vmware, but I want to test anything that is small enough and with a browser access to make it less of a pain to manage  it. Thanks.

---

### Post by jaime256 on 2010-07-20
Here's what I get when I try to install from the dvd drive directly...why does the dvd point to a temp directory is beyond me...that's what it sees from a default installation.

---

### Post by jaime256 on 2010-07-20
For anyone else that may be interested on this. I decided to give the "Free" version from xensource a try. As it turns out the openxenmanager seems to work with this version which is 5.6.0 I think is the latest version. However this openxenmanager doesn't work with the xen.org cloud version which I was trying before. I'm currecntly installing this vm to test it out and everything on my workstation and laptop is the same. I haven't changed anything so I am using the same programs I downloaded. I hope this helps. So again, everything inlcuding my samba shares seem to be working without a problem as of now, but I just re-installed everything on the server. I should also note that now I also see the total hard drive size. On the cloud version I only saw 8 gigs total and maybe that also had something to do with my problem. I don't know but it just wouldn't work.

I just finished the install and when the system asked me to remove the disk (iso) in this case. I noticed the storage was at empty. I forgot to look at this while it was installing so I was surfing the web. Needless to say I went ahead and tried to change the storage to dvd and poof, the openxenmanager closed on me. I just had to run it again and I'm back on right where I was. So this still has a bug somewhere, but if anyone has any idea of how to get a nice shortcut to this, please let me know. I tried adding one to the panel but it just would not work so I hope someone can make one.

---

### Post by jaime256 on 2010-07-20
I'm now trying to change the memory on the Ubuntu vm I just installed and It just won't change. It's a bit slow so I just wanted to give it a little bit more memory. Here's the message I get. I'm just trying to double the memory this uses since I know I have plenty on this machine. Does anyone know if you need to install a linux pack for this "Free" version?

{'Status': 'Failure', 'ErrorDescription': ['MEMORY_CONSTRAINT_VIOLATION', u'Memory limits must satisfy: static_min \u2264 dynamic_min = dynamic_max = static_max']}
Exiting...

---

### Post by jaime256 on 2010-07-20
Windows XP SP2 install. I wanted to see what this would do so I put in the windows cd on the local dvd of that server and tried to install my windows xp on a virtual machine...After I start the vm, it either freezes or closes the openxenmanager. Here's the error I see on the terminal when I try to install this...

The program 'window.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 42521 error_code 9 request_code 140 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I restarted the openxenmanager and now I can see the install blue screen...although not perfect this "Free" version of xen and openxenmanager at least let me get started without having to figure out why nothing installs and just spits out errors that I can't find anything to. Okay, it's still spitting out errors, but at least I can now install something.

---

### Post by jaime256 on 2010-08-01
Today I decided to change the static IP on the server from the console. Unfortunately it will not work remotely or from the console. I get "Configuration Failed: Internal Error: Failure("Management interface has no IP address") even though I manually put in the information it just won't take it. I decided to try the old ip address even though I changed the server name as well and that one worked fine again. I rebooted the server a few times then change the ip address from the console, but the server still won't take the new ip on the same network which is pretty odd to say the least. If anyone has any idea please post. Xen server is getting to be a real headache and I'm just testing it. I'm trying to find something that hopefully just works. Thanks.

---

