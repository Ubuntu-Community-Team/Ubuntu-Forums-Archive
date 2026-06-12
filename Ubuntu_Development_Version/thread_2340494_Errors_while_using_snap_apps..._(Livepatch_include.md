---
title: "Errors while using snap apps... (Livepatch included)"
date: 2016-10-19
forum: Ubuntu Development Version
---

### Post by zika on 2016-10-19
After succefull install of snap I get```
:~$ sudo canonical-livepatch enable ___2016/10/19 11:09:41 Error executing enable?auth-token=___.
Connection to the daemon failed: Put http://127.0.0.1/enable?auth-token=___: dial unix /var/snap/canonical-livepatch/15/livepatchd-priv.sock: connect: no such file or directory
:~$ canonical-livepatch status
Connection to the daemon failed: Get http://127.0.0.1/status?verbose=false: dial unix /var/snap/canonical-livepatch/15/livepatchd.sock: connect: no such file or directory
```I must be doing something wrong... ;)

---

### Post by kagashe on 2016-10-19
You need to get the token:
 Go to [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch) and retrieve your livepatch
token, for example: d3b07384d213edec49eaa6238ad5ff00

Then apply it:
sudo canonical-livepatch enable d3b07384d113edec49eaa6238ad5ff00

Kamalakar

---

### Post by zika on 2016-10-19
> **kagashe said:**
> You need to get the token:
 > Go to [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch) and retrieve your livepatch
token, for example: d3b07384d213edec49eaa6238ad5ff00

Then apply it:
sudo canonical-livepatch enable d3b07384d113edec49eaa6238ad5ff00

KamalakarOf course I did supply proper token, it was just, for sanity reasons, erased from a log I gave, marked with ___ instead... ;)
As You can, also, see it does not complain about token, did not get to it yet...
Update&#8321;: I do suspect proxy support in snap so I'll try that at home, without any proxy, once I get there... ;)
Update&#8322;: Nope, the same error on machine/environment where proxy is not an issue...

---

### Post by mc4man on 2016-10-19
If this is for 16.10 what would indicate that it is supported?

---

### Post by valtam on 2016-10-19
Got to this point, no further:

```
Connection to the daemon failed:Put http://127.0.0.1/enable?auth-token=xxxx: dial unix /var/snap/canonical-livepatch/15/livepatchd-priv.sock: connect: no such file or directory
```

---

### Post by zika on 2016-10-20
> **mc4man said:**
> If this is for 16.10 what would indicate that it is supported?look above (right, bottom):
zika:[B]Distro:
[/B][RIGHT][COLOR=#000000]Ubuntu Development Release[/COLOR][/RIGHT]
[https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941](https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941)
> **zika said:**
> Having &#8222;devel&#8220; in all source files brought this to my attention:```
~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:printing-9.20160110ubuntu5-amd64:printing-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID: Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:        17.04
Codename:       zesty
```Al(l_)ready... ;)


Update&#8321;: After upgrade to new version of snapd (2.16+16.10ubuntu1.1) message changed to:```
cannot change apparmor hat of the support process for mount namespace capture. errmsg: Operation not permitted
support process for mount namespace capture exited abnormally
```and no snap installed works giving the same mistake...
Update&#8322;: [https://launchpad.net/~snappy-dev/+archive/ubuntu/edge](https://launchpad.net/~snappy-dev/+archive/ubuntu/edge) (snapd (2.16+ppa57.6c8c5e38-1)) brings me back to aparrmor error given above...

---

### Post by mc4man on 2016-10-20
> **zika said:**
> look above (right, bottom):
zika:[B]Distro:
..
Then read here


> Q: What about other releases of Ubuntu?
A: The Canonical Livepatch Service is provided for Ubuntu 16.04 LTS’s Linux 4.4 kernel. Older releases of Ubuntu will not work, because they’re missing the Linux kernel support. Interim releases of Ubuntu (e.g. Ubuntu 16.10) are targeted at developers and early adopters, rather than Long Term Support users or systems that require maximum uptime.  We will consider providing livepatches for the HWE kernels in 2017.

---

### Post by zika on 2016-10-20
> **mc4man said:**
> Then read hereKnow and read that.> **zika said:**
> and **no snap installed** works giving the same mistake...
Update&#8322;: [https://launchpad.net/~snappy-dev/+archive/ubuntu/edge](https://launchpad.net/~snappy-dev/+archive/ubuntu/edge) (snapd (2.16+ppa57.6c8c5e38-1)) brings me back to aparrmor error given above...
Update&#8321;: changed the name of the thread not to trigger complaints...

---

### Post by cariboo on 2016-10-20
I just installed the live patch on my 16.04 server the output looks like this:

```
cariboo@willy:~$ sudo canonical-livepatch enable XaXXXbXXXeXXXXXXaXXaXXXXaXXcXXX
Successfully enabled device. Using machine-token: XXaXdXfeXXXXXXXaXXXXXdXdXaXcXaX
```

---

### Post by zika on 2016-10-20
snapd (2.16+ppa58.dff47722-1)
It solved issues with other snaps... ;)
It brought back error message about 127.0.0.1 in attempt to use livepatch.
Back to drawing board as soon as I do get a tad of spare time to see what is a hidden culprit, aside from disclaimer about 17.04... ;)

---

### Post by Lester_Ingber on 2016-10-21
I'm running 16.04 on a Linode VPS.  I tried installing livepatch, but it failed.  I do have apparmor installed (but have not used it).

```
# snap install canonical-livepatch4.34 MB / 4.34 MB [==================================================] 100.00 % 1.25 MB/serror: cannot perform the following tasks:- Setup snap "ubuntu-core" 
(423) security profiles (no state entry for key)- Setup snap "canonical-livepatch" 
(15) security profiles (cannot setup apparmor for snap "canonical-livepatch": cannot load apparmor profile "snap.canonical-livepatch.canonical-livepatch": cannot load apparmor profile: exit status 
1apparmor_parser output:Cache read/write disabled: interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)Warning: unable to find a suitable fs in /proc/mounts, is it mounted?Use --subdomainfs to override.)- Setup snap "canonical-livepatch" 
(15) security profiles (cannot load apparmor profile "snap.canonical-livepatch.canonical-livepatch": cannot load apparmor profile: exit status 1apparmor_parser output:Cache read/write disabled: interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)Warning: unable to find a suitable fs in /proc/mounts, is it mounted?Use --subdomainfs to override.
```

---

### Post by #&amp;thj^% on 2016-10-27
This just in:
Dustin Kirkland has announced Canonical is rolling out a live kernel update feature for Ubuntu users. The new feature, called kernel live patching, will allow Ubuntu users to upgrade their running kernels without rebooting their computer. "Kernel live patching enables runtime correction of critical security issues in your kernel without rebooting. It's the best way to ensure that machines are safe at the kernel level, while guaranteeing uptime, especially for container hosts where a single machine may be running thousands of different workloads. We're very pleased to announce that this new enterprise, commercial service from Canonical will also be available free of charge to the Ubuntu community. The Canonical Livepatch Service is an authenticated, encrypted, signed stream of livepatch kernel modules for Ubuntu servers, virtual machines and desktops." Details on how to enable kernel live patching can be found in Kirkland's mailing list post. 

And from the mailing list post
```
Canonical enterprise kernel livepatch service, free to Ubuntu community!
Dustin Kirkland kirkland at canonical.com
Tue Oct 18 18:02:06 UTC 2016
Kernel live patching enables runtime correction of critical security
issues in your kernel without rebooting. It’s the best way to ensure
that machines are safe at the kernel level, while guaranteeing uptime,
especially for container hosts where a single machine may be running
thousands of different workloads.

We’re very pleased to announce that this new enterprise, commercial
service from Canonical will also be available free of charge to the
Ubuntu community.

The Canonical Livepatch Service is an authenticated, encrypted, signed
stream of livepatch kernel modules for Ubuntu servers, virtual
machines and desktops.

Community users of Ubuntu are welcome to enable the Canonical
Livepatch Service on 3 systems running 64-bit Intel/AMD Ubuntu 16.04
LTS.  (To enable the Canonical Livepatch Service on more than 3
systems, please see http://ubuntu.com/advantage for commercial support
subscriptions starting at $12 per month.)

On an up-to-date, 64-bit Ubuntu 16.04 LTS system, you can enable the
Canonical Livepatch Service today in 3 simple steps:

(1) Go to https://ubuntu.com/livepatch and retrieve your livepatch
token, for example: d3b07384d213edec49eaa6238ad5ff00

(2) Install the livepatch snap, like this:
   $ sudo snap install canonical-livepatch

(3) Enable your account with the token from step 1
   $ sudo canonical-livepatch enable d3b07384d113edec49eaa6238ad5ff00

That’s it.  You’re up and running!  You can check your status at any 
time with:

   $ canonical-livepatch status
   kernel: 4.4.0-38.57-generic
   fully-patched: true
   version: "12.2"

Now your kernel will remain securely patched, and you can reboot when
it’s convenient for you.

For more detailed technical information, screenshots, and a demo, see
my blog post at:
  * http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html

And see the official landing page at:
  * http://www.ubuntu.com/server/livepatch

Cheers,

Dustin Kirkland
(on behalf of dozens of my colleagues at Canonical who are the brains
and brawn behind this amazing work! )


```
Happy Patching!:)
Cavsfan ought to be a very happy person now!

---

### Post by admiralanal on 2016-10-27
Wonderfull product , except : 

sudo canonical-livepatch enable <token>
sudo: canonical-livepatch: command not found
openflixr@openflixr:~$ sudo /snap/bin/canonical-livepatch enable <token> 
cannot change apparmor hat of the support process for mount namespace capture. errmsg: Operation not permitted

---

### Post by danc-dccathome on 2016-10-28
I get this error:
```
Connection to the daemon failed: Put http://127.0.0.1/enable?auth-token=ef68d21a86184c08b39fa74dac4b2d8d: dial unix /var/snap/canonical-livepatch/15/livepatchd-priv.sock: connect: no such file or directory
```

---

### Post by zika on 2016-10-28
> **danc-dccathome said:**
> I get this error:
```
Connection to the daemon failed: Put http://127.0.0.1/enable?auth-token=ef68d21a86184c08b39fa74dac4b2d8d: dial unix /var/snap/canonical-livepatch/15/livepatchd-priv.sock: connect: no such file or directory
```Remove a quote of Your token... ;)

---

### Post by ventrical on 2016-10-28
ehehehe...

```

Successfully enabled device. Using machine-token:

```

uhh... it was a little baffling  how the first time visit to the  webpage knew who I was :)

Regards..

---

### Post by ventrical on 2016-10-28
> **admiralanal said:**
> Wonderfull product , except : 

sudo canonical-livepatch enable <token>
sudo: canonical-livepatch: command not found
openflixr@openflixr:~$ sudo /snap/bin/canonical-livepatch enable <token> 
cannot change apparmor hat of the support process for mount namespace capture. errmsg: Operation not permitted

Did you skip this step?

```

$ sudo snap install canonical-livepatch


```

---

### Post by jimmy-frydkaer on 2016-10-28
I too get a "no such file or directory" error

---

### Post by admiralanal on 2016-10-28
No , i have installed that :)

aa-status gives me 2 enabled profiles .

---

### Post by kevdog on 2016-10-28
Stinks that its only for 64bit :(

---

### Post by bearlake on 2016-10-28
Tried it on 17.04 first thinking it wouldn't work and it failed.

Tried it on 16.04 and got this. :)

```
$ canonical-livepatch status
kernel: 4.4.0-45.66-generic
fully-patched: true
version: ""
```

---

### Post by #&amp;thj^% on 2016-10-29
> **ventrical said:**
> Did you skip this step?

```

$ sudo snap install canonical-livepatch


```

he he Had to try it before up-grading the kernel 
Results:
```
canonical-livepatch status
kernel: 4.4.0-31.50-generic
fully-patched: true
version: "13.3"

```
And remember this.
> _On an up-to-date, 64-bit Ubuntu 16.04 LTS_ system,  
Regards

---

### Post by admiralanal on 2016-10-29
> **1fallen said:**
> he he Had to try it before up-grading the kernel 
Results:
```
canonical-livepatch status
kernel: 4.4.0-31.50-generic
fully-patched: true
version: "13.3"

```
And remember this.

Regards 
I have installed snap but still get that error.
/snap/bin is in my $PATH , but when i run sudo canonical-livepatchsudo: canonical-livepatch: command not found



Running 16.04.1 server

---

### Post by kendall-green on 2016-10-29
same problem with live-patch.  connection refused.

---

### Post by slickymaster on 2016-10-29
Merged [this thread]("https://ubuntuforums.org/showthread.php?t=2341379") with this one.

---

### Post by #&amp;thj^% on 2016-10-29
It seems like they are trying... and they are aware of some of the issues happening: [https://answers.launchpad.net/ubuntu/+source/canonical-livepatch/+question/403292](https://answers.launchpad.net/ubuntu/+source/canonical-livepatch/+question/403292)
Proxys seem to cause some of the issues.
But I see no errors behind a VPN service here.
They are also having problems with bug reports being generated ATM...so some patience might be needed here.
When they get it fixed you can generate a bug report if needed with:
```
ubuntu-bug canonical-livepatch
```
But it might be helpful to give them some time to fix this before flooding them with bug reports for now;).

---

### Post by mc4man on 2016-10-29
> **danc-dccathome said:**
> I get this error:
```
Connection to the daemon failed: Put http://127.0.0.1/enable?auth-token=ef68d21a86184c08b39fa74dac4b2d8d: dial unix /var/snap/canonical-livepatch/15/livepatchd-priv.sock: connect: no such file or directory
```

That error is from _installing the snap before updating_ to latest snapd, apparmor, ubuntu-core-launcher & snap-confine.
You'd need to get updated, remove the snap, then install the snap again.

---

### Post by #&amp;thj^% on 2016-10-29
Ok just doing some testing with unsupported kernels (from the information that is already said in this thread)
What I did was install a 4.8 low lat series kernel here...Results:
```
canonical-livepatch status
kernel: 4.8.0-040800-lowlatency (unsupported)
fully-patched: false
version: ""

me@me-System-Product-Name:~$ sudo canonical-livepatch enable <snip token>
[sudo] password for me: 
2016/10/29 11:09:53 Error executing enable?auth-token=<snip token>
Machine-token already exists! Please use 'disable' to delete existing machine-token.

me@me-System-Product-Name:~$ sudo canonical-livepatch disable <snip token>
Successfully disabled device. Removed machine-token: <snip token>

me@me-System-Product-Name:~$ sudo canonical-livepatch enable <snip token>
Successfully enabled device. Using machine-token: <snip token>

me@me-System-Product-Name:~$ canonical-livepatch statuskernel: 4.8.0-040800-lowlatency (unsupported)
fully-patched: true
version: ""

```
Note: VPN Service active while doing the above.
```
uname -a && lsb_release -a
Linux me-System-Product-Name 4.8.0-040800-lowlatency #201610022031 SMP PREEMPT Mon Oct 3 00:38:25 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


```

---

### Post by admiralanal on 2016-10-31
Still not working here , followed all directions .. still that apparmor error :/
Anyone?

---

### Post by #&amp;thj^% on 2016-10-31
Have you looked in your logs for a meaningful error?
And just a suggestion here...have you tried disabling apparmor just long enough to get your Livepatch service.

---

### Post by lbesselink on 2016-11-09
I wanted to try live-patching, so I made a freshly installed ubuntu server [COLOR=#000000]16.04.1 LTS ([/COLOR][COLOR=#000000]xenial[/COLOR][COLOR=#000000]) from iso/cd without updates installed.

[/COLOR]But I got the error:

```
Snappy kernel-module-control interface not connected!
Snappy kernel-module-control interface not connected!audit: type=1400 audit(1478730114.441:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=2597 comm="apparmor_parser"audit: type=1400 audit(1478730114.441:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=2597 comm="apparmor_parser"audit: type=1400 audit(1478730114.441:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=2597 comm="apparmor_parser"
apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=2597 comm="apparmor_parser"

systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Unit entered failed state.
systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Failed with result 'exit-code'.
systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Service hold-off time over, scheduling restart.
systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
```


Here is what I did to fix it:

- installed all the updates (except for the kernel), by running apt-get update && apt-get -du dist-upgrade && apt-get install every-package-that-was-listed-except-for-kernel-updates
- reboot (ironically ! not sure if this is necessary though)
- removed the 'snap' for livepatching, by running: [COLOR=#000000]snap remove canonical-livepatch[/COLOR] 
- installed it again: [COLOR=#000000]snap install canonical-livepatch
- and ran [/COLOR][COLOR=#000000]canonical-livepatch enable some-id[/COLOR]

[COLOR=#000000]And it immediately downloaded and applied the kernel patches

So I assume one of the updates installed fixes it. I don't know which one yet though. Just installing the updates of [/COLOR][COLOR=#000000]snapd apparmor might not be enough, I also had other updates like: [/COLOR][COLOR=#000000]libapparmor1 [/COLOR][COLOR=#000000]libapparmor-perl [/COLOR][COLOR=#000000]libapparmor1:amd64 [/COLOR][COLOR=#000000]libapparmor-perl:amd64 [/COLOR][COLOR=#000000]liblxc1[/COLOR]

---

### Post by tobias-boyd on 2016-12-01
I am having the same problem - I've tried on two different 16.04.1 machines, same symptoms exactly: ```
sudo snap install canonical-livepatch
``` runs fine, but ```
sudo canonical-livepatch enable ID
``` throws 'command not found'. Both machines are up to date (i.e. running ```
sudo apt-get dist-upgrade
``` returns '0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.') I've tried removing and reinstalling the snap with no effect.

---

### Post by #&amp;thj^% on 2016-12-02
I have no solution to those having troubles...but I had also suggested to temporarily disable "[COLOR=#000000]apparmor[/COLOR]"...and just to confirm _this will **NOT WORK**_...it seems [COLOR=#000000]apparmor and livepatch are connected to each other.
Thought it was important enough to Note Here in this thread.
Regards
[/COLOR]

---

### Post by tobias-boyd on 2016-12-02
I got it working, it looks to me like there are some problems running snaps with sudo; it's pretty clearly related to your path - I  had added /snaps/bin to mine with no luck, but just running

```
sudo /snap/bin/canonical-livepatch enable ID
```

was succesful, finally!

---

### Post by ventrical on 2016-12-02
> **1fallen said:**
> he he Had to try it before up-grading the kernel 
Results:
```
canonical-livepatch status
kernel: 4.4.0-31.50-generic
fully-patched: true
version: "13.3"

```
And remember this.

he he Had to try it before up-grading the kernel 
Results:
 	Code:
 	canonical-livepatch status
kernel: 4.4.0-31.50-generic
fully-patched: true
version: "13.3" 
And remember this.
 	 		 			 			 				_On an up-to-date, 64-bit Ubuntu 16.04 LTS_ system, 			 		
 	
 
Regards 				 			  			   		 			 				 			 			 				

Regards

Trying some different things with different versions. Your last statement has to be followed to a 't'. There is no leeway that i can find :)

Regards..

---

### Post by #&amp;thj^% on 2016-12-02
> **tobias-boyd said:**
> I got it working, it looks to me like there are some problems running snaps with sudo; it's pretty clearly related to your path - I  had added /snaps/bin to mine with no luck, but just running

```
sudo /snap/bin/canonical-livepatch enable ID
```

was succesful, finally!
Thanks for Sharing...hoping for more folks to confirm this method...and not just a glitch with canonical-livepatch service. 

> **ventrical said:**
> Trying some different things with different versions. Your last statement has to be followed to a 't'. There is no leeway that i can find :)

Regards..

:smile: I have tried to reproduce the errors being reported here... but I just can not. Even with unsupported kernels Just Shows 
```
canonical-livepatch statuskernel: 4.8.0-040800-lowlatency [COLOR=#ff0000](unsupported) [/COLOR]fully-patched: true
```
So I'm just Stumped.:confused:

---

### Post by ventrical on 2016-12-02
> **1fallen said:**
> Thanks for Sharing...hoping for more folks to confirm this method...and not just a glitch with canonical-livepatch service. 



:smile: I have tried to reproduce the errors being reported here... but I just can not. Even with unsupported kernels Just Shows 
```
canonical-livepatch statuskernel: 4.8.0-040800-lowlatency [COLOR=#ff0000](unsupported) [/COLOR]fully-patched: true
```
So I'm just Stumped.:confused:

What I did is to try and install it in zesty (unity8+xmir) and within a Libertine container(yakkety) using UXterm. It fails from both the terminal click app in unity8 and in libertine container. Cannot mount snap .. no socket .. etc..  so my comment was specific to your posted instruction about fully updated 16.04!! The option will otherwise break or not be available. So this service is for commercial clients and most likely stable xenial only.

Regards..

---

### Post by #&amp;thj^% on 2016-12-02
> **ventrical said:**
> What I did is to try and install it in zesty (unity8+xmir) and within a Libertine container(yakkety) using UXterm. It fails from both the terminal click app in unity8 and in libertine container. Cannot mount snap .. no socket .. etc..  so my comment was specific to your posted instruction about fully updated 16.04!! The option will otherwise break or not be available. _**So this service is for commercial clients and most likely stable xenial only**_.

Regards..
Oh Yes!:) Sorry if I was unclear on that. all of my efforts to reproduce the "errors reported here" has been with **16.04.1 only.**
Good to see you posting again Old Friend. And I know Life can take over any free time.:)
Best Regards

---

### Post by ventrical on 2016-12-02
> **1fallen said:**
> Oh Yes!:) Sorry if I was unclear on that. all of my efforts to reproduce the "errors reported here" has been with **16.04.1 only.**
Good to see you posting again Old Friend. And I know Life can take over any free time.:)
Best Regards

No apology necessary. My point it that you were very clear. I was just trying to break it in other versions ... and it did.

Life.

Yes... we had a warm autumn and the grass at the airfield I manage needed to be cut because some aircraft like C172 or ultralights need a trim runway.  I caught a draft... coughing .. hacking  (and yes the other hacking too ) :)  and working on this wireless IoT mixer  by Shure.... ahhh .. what a mess....but I haven't left.  Just frustrated with unity8 and containers , slow progress of convergence .. and now I am completely off topic :) heheaheahehhhe

Regards..

---

### Post by tk83 on 2017-01-06
> **tobias-boyd said:**
> I got it working, it looks to me like there are some problems running snaps with sudo; it's pretty clearly related to your path - I  had added /snaps/bin to mine with no luck, but just running

```
sudo /snap/bin/canonical-livepatch enable ID
```

was succesful, finally!

This fixed it for me on:
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

Have you raised a bug against snapd about this? It looks like something the devs should be aware of

---

