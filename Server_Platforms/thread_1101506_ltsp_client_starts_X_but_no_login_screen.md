---
title: "ltsp client starts X but no login screen"
date: 2009-03-20
forum: Server Platforms
---

### Post by richard_parker_va on 2009-03-20
We have an Ubuntu 8.10 LTSP server, fully updated. We have several PXE clients working quite well--no issues. Works great. Love it.

_Newer clients working, older clients no login_
However, there are another set of clients which are booting, setting up the LTSP client and even starting X, but failing at that point--they do not reach the ltsp (ldm?) login screen but instead seem to be stuck in a loop which changes the tty (console) selection between:

a) A screen which has the classic X startup screen-- X for a mouse pointer (mouse movement works), but nothing else;

b) A text screen "xauth: creating new authority file /var/run/ldm-xauth-JyUWQ3592" 

If I press Alt-F1 during the splash screen to monitor the progress, it ends up in a 3-screen loop of the above plus tty1, which shows, after the progress of startup, the text login to the client machine (not the login to the server--this is the local client login).

_Client boots correctly, but fails before/at login or ldm_
The client is definitely booting correctly, it mounts the filesystem and gets through at least S25ltsp-client-core of runlevel rc2.

/var/log/syslog on the ltsp server shows that every 15 seconds or so (the time to do the above referenced loop) the client connects to the ldminfod daemon:

```
Mar 20 10:30:23 ltspservername ldminfod[12345]: connect from 10.10.10.10
```


_Where are ltsp client log files?_
My biggest point of loss is that I can't seem to find out whether or where any log files are so I can get more detailed information to nail down the problem.  Are there log files for the client boot? syslog? that sort of thing? The chroot filesystem on the server is readonly...


_Is client's video card the problem?_
I'm suspecting something to do with the display setup, but this is pure conjecture given where the failure seems to occur.

Note that the ltsp server is working and we have several clients working. The client I am now trying to start used to have Dapper on it, but it is rather old. If I start a small debian OS on it, lspci indicates the VGA controller is an "S3 Inc. 86c325 [ViRGE] (rev 02)"


Sorry about the long post, but hopefully I have included all the information which may be helpful if someone has seen this behaviour before or can point me to the logs.

---

### Post by richard_parker_va on 2009-04-24
I've done a lot of work on this over the past several weeks and, though I've made progress, we don't have the older hardware up and running yet.

It turns out the problem is X related--I installed ubuntu 8.1 directly on this hardware and the same problem happened as a direct install. Furthermore, when booting from ltsp, the client was actually connecting correctly and loading the OS image, etc. I authorized root access on the client and can login and work off the client no problem, but no X.

Reviewing the logs (Xorg.7.log), the X server crashes with signal 4. The loop referred to in the previous post turns out to be because the ldm script is supposed to keep coming around to the greeter once the user logs out -- but because X is crashing, it keeps trying to start the greeter with no success.

It turns out, given other internet research, that the core problem stems from a combination of the older i/o hardware and that the client cpu does not have sse support. Others have solved the problem by going back to xserver-common v. 1.3.97 -- intrepid uses 1.5.2.

I tried to solve this by: setting up a new chroot for the older hardware (dhcp checks the MAC address and points it to the 'oldi386' chroot for all of the older machines). We built a new client image, etc. and did a downgrade with apt to hardy for the Xorg related packages. This worked superficially, but the xserver-common version is 1.4+, so, unfortunately, it didn't solve the problem.  The gutsy repository seems to be gone, so unless someone knows where that is, that doesn't look like an option. 

Other people may have the same problem or be able to suggest a solution. I think I'm down to maybe 5 options: 
[LIST=1]
[*] give up on the old hardware and be happy ltsp works great with newer hardware (don't like this option, given that one of the motivations for setting up ltsp was to use the older hardware); 
[*] apparently rebuilding xserver-common with certain flags (I need to check what they are again, but saw them referenced in a forum where people were having this same problem). However, I haven't done any of  that sort of thing for a long time and I don't know where to get the source); 
[*] find a gutsy repository, downgrade to gutsy level X packages and hope that works;
[*] possibly build a debian etch client chroot? Can I have a debian etch client chroot when the ltsp server is ubuntu?
[*] is there some other way to avoid the sse support problem altogether with some flags or some other option under Xorg / lts.conf which I have not otherwise found documented?
[/LIST]

---

### Post by richard_parker_va on 2009-05-22
For those interested in the culmination of the above saga, it turns out I was right in my second post--the problem was related to a Xorg feature/bug that existed between versions 1.3.98 and 1.5.x. It looks like it was corrected/changed in 1.6.  

Thus, we upgraded our ltsp server to ubuntu Jaunty (v 9.04) which includes xorg 1.6.0. We rebuilt the client chroot (ltsp-build-client) and made sure everything was fully updated.

Result?  The older clients now work, with the exception of sound problems which I think is just a driver issue we'll need to figure out.

---

