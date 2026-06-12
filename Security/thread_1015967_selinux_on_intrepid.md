---
title: "selinux on intrepid"
date: 2008-12-19
forum: Security
---

### Post by quark_77 on 2008-12-19
Hi All,

I'm having some issues running SELinux on Intrepid. The issue is this: when I run SELinux in enforcing mode, I can't do anything. I fully understand that's the point of SELinux in some regards, but I get messages like these:
[LIST]
[*]Unable to switch to tty1: permission denied
[*]Unable to execute /bin/bash: permission denied
[/LIST]
I know what's happening: SELinux is blocking these applications, ```
cat /var/log/syslog | grep 'avc'
``` will tell me that. So the problem is: how do I fix this situation?

I'm going to explain what I've done so far as well, as perhaps there's something I've missed here. 

[LIST=1]
[*]I was running 8.04 earlier this year which lets you just ```
sudo apt-get install selinux
```. However, on intrepid, that doesn't seem to work (i.e. installs no policy) which is interesting. Anyway, I installed selinux-policy-default which pulled all it's dependencies in i.e. setools.
[*]This didn't work and I realised from my last exploration you have to have a running selinux kernel first. So I set about selinux=1'ing it into existence.
[*]I found that actually the initramfs scripts are broken in /etc/initramfs-tools/scripts/init-bottom/_load_policy (see [https://bugs.launchpad.net/ubuntu/+source/selinux/+bug/277030](https://bugs.launchpad.net/ubuntu/+source/selinux/+bug/277030)) and fixed it for my system, regenerated the initramfs.
[*]I added selinux=1 to the defopts in /boot/grub/menu.lst and ran update grub, so now all kernels will be selinux-enabled.
[*]Loaded up with the new all-powerful kernel and re-installed selinux-policy-default just to make sure. I don't get asked about .tc files (I did on Hardy) as described here: [http://mctalby.mc.man.ac.uk/~mc/_unix_security/unix_sec_kernel_selinux.SE_Linux.html](http://mctalby.mc.man.ac.uk/~mc/_unix_security/unix_sec_kernel_selinux.SE_Linux.html) . 
[*]Reboot. We are still in permissive mode. Check with sestatus:
```
sestatus
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   permissive
Mode from config file:          permissive
Policy version:                 23
Policy from config file:        default
```
[*]OK, now reboot, edit grub on the fly adding enforcing=1 to the end of the boot line and boot. Hey presto, up comes X, or a tty, but gnome sessions last less than 10 seconds and ttys give the above error.
[/LIST]

I should also add that I modified /etc/pam.d/login, changing the word on the end of pam_selinux.so from close (which denied access to X11 also!) to multiple (implying give me a choice on a MLS system). I will try removing multiple too.

I suppose I could use audit2allow to enable all the things being denied to be allowed but there are such a number of avc errors I'm not convinced that would necessarily be secure... might as well not run selinux at all.

Any ideas? What am I doing wrong please? 

I may be wrong... but it appears the full policy isn't implemented, hence why simple things are denied? Or am I missing something? Can I install the refpolicy myself and if so does anyone know of any tutorials for doing so on ubuntu/debian?

Thanks in advance for anything you have!

P.S. I don't want to use AppArmor, I am aware it exists, is easier, installed and enabled by default and all that. I'm also aware Fedora has working SELinux... I am tempted, but prefer Ubuntu's way of doing things at the moment, plus 8.04 SELinux worked for me.

Quark_77

---

### Post by bodhi.zazen on 2008-12-19
It depends on how much time you wish to spend debugging the SELinux policies.

IMO, if you wish to use SELinux I would re-examine the choice to run Fedora. I am currently running Fedora 10 and it is a fine OS. In some ways Fedora is superior to Ubuntu and in others Ubuntu is superior. IMO it is best to be flexible and I can say, after doing this for some time, it is not *that* hard to switch distros.

Fedora has some very nice tools to debug SELinux as well. So, IMO, if I were weighing the difference / hassle factor, I think it will be more hassle for you to re-write the SELinux policies on Intrepid then switch to Fedora.

Another "problem" with Ubuntu, you are unlikely to fine many on these forums with much experinece with SELinux (it can be hard enough with AppArmor).

As a "one pager" I found this quite helpful :

[http://wiki.centos.org/HowTos/SELinux](http://wiki.centos.org/HowTos/SELinux)

---

### Post by kevdog on 2008-12-19
bodhi

What distros are you running now?  It sounds like you have a few machines?

---

### Post by bodhi.zazen on 2008-12-19
> **kevdog said:**
> bodhi

What distros are you running now?  It sounds like you have a few machines?

:lolflag: I dabble in several distros, always nice to learn a new trick.

At the moment I run virtualization (the over head is low with openvz) :

Centos 5.1, Fedora 10, Ubuntu 8.04, Ubuntu 8.10, and 9.04 Alpha. I have Wolvix on an old laptop as well.

---

### Post by quark_77 on 2008-12-19
> **bodhi.zazen said:**
> 
IMO, if you wish to use SELinux I would re-examine the choice to run Fedora...

I'm beginning to consider that to be honest. I like Ubuntu and the way it works and would like to stick with it, but at the same time I think I'm going to look at Fedora. Ubuntu Hardened doesn't seem to be doing SELinux well at the moment. Something else I noticed, selinux package conflicts with selinux-policy-default... ?!

> **bodhi.zazen said:**
> 
I think it will be more hassle for you to re-write the SELinux policies on Intrepid then switch to Fedora.

Are we saying, basically, that the policies weren't updated/packaged for Intrepid? That would be a shame. I assume I can't just pull the package from Hardy, unpack the policy and it's .te files and try that.

> **bodhi.zazen said:**
> 
Another "problem" with Ubuntu, you are unlikely to fine many on these forums with much experinece with SELinux (it can be hard enough with AppArmor).
No, which is a shame. I asked [about selinux] pre 8.04 and nobody answered it... Hardy was good because I could use enforcing mode with a full policy.

Does anybody have SELinux working on Intrepid?

Thanks everyone.

---

### Post by quark_77 on 2008-12-19
All,

I came up with a new idea:
```
sudo apt-get install selinux-policy-src
cd /usr/src
tar -xvf selinux-policy-src.tar.gz
```
Then compile from source. (make, then make install, then make load).

I personally set the policy to standard (not mls/mcs) and to monolithic which generates a policy.n file in /etc/selinux/'name of policy'/policy/policy.23

This policy also loads, unfortunately it denies mount permission to access anything under /dev/mapper/ thereby killing cryptsetup startup for my encrypted /home.

Looks like you are right bodhi.zazen... I'll either be modifying the policy all the time or I'll have to change to Fedora.

Anybody any other ideas?

Thanks,

Quark_77

---

### Post by clarejarvis on 2008-12-26
quark_77,

I have tried something very similar.   I install II and did several apt-gets for various selinux packages.   I set selinux=1 and enforcing=0 in menu.lst.   I have logged in and done a sudo su.
I have tried newrole -t sysadm_t and that works but I cannot do
newrole -r sysadm_r   and I get an invalid context message.   It seems that I am stuck in the unconfined_u and do not know how to get to sysadm_u.   Anyway I can see that things are not going to work but I have tried setenforce 1 and I get immediately logged out without proper permissions for /bin/bash.

I have tried downloading ref-policy and compiling it and it compiles nicely but I get run-time errors.   I have not been able to compile a policy downloaded from ubuntu.   

I have edited config:

SELINUX=enforcing
SELINUXTYPE=default
SETLOCALDEFS=1


I have edited /etc/selinux/default/users/local.users

user clare roles { user_r staff_r sysadm_r };

Do you see anything wrong with these?

Clare Jarvis

---

### Post by clarejarvis on 2008-12-29
I abandoned my experiments with intrepid :(.   I installed hardy and selinux and am making more progress :).   I have used semange to:

semanage login -m -s staff_u johnd

but when johnd logs in then .bash_profile and .bash_logout will not execute.   (obivously selinux is doing something).   But if I use semanage to:
semanage login -m -s unconfined_u johnd  
then .bash_profile and .bash_logout work normally.   I still cannot get newrole to do anything useful.   How do I get a login with multiple roles?   Could you provide examples of using semange and newrole or any other process that will assist?


Thanks and Happy New Year :popcorn:

---

### Post by bodhi.zazen on 2008-12-29
Not sure of the details you are running , see if these links help :

[http://www.gentoo.org/proj/en/hardened/selinux/selinux-handbook.xml?part=3&chap=1](http://www.gentoo.org/proj/en/hardened/selinux/selinux-handbook.xml?part=3&chap=1)

[http://www.ibm.com/developerworks/linux/library/l-rbac-selinux/](http://www.ibm.com/developerworks/linux/library/l-rbac-selinux/)

---

### Post by clarejarvis on 2008-12-30
Thanks for your help, bodhi.zazen.   I now have this problem:

If I type in:
newrole -r sysadm_r

I get the error message:
Cannot find your entry in the shadow passwd file.


I tried resetting the password using   passwd but that did not help.

How do I update the shadow passwd file?

---

### Post by tgilber1 on 2009-01-21
I had trouble installing selinux and getting it to work.  The following command:

sudo apt-get install selinux

installed selinux and selinux-policy-dummy.  Consequently, selinux was not enabled because of the lack of a policy folder in the /etc/selinux directory.  Additionally, during boot, a load_policy file not found error occurred after the init process started.  The problem was the _load_policy script in the /etc/initramfs/scripts/init-bottom was pointing to the wrong directory.  I changed it from /sbin/policy to /usr/sbin/load_policy and ran the following command

sudo update-initramfs -u -k `uname -r`

Nevertheless, there was no policy in the etc directory.  I tried to install "sudo apt-get install selinux-policy-default", which proceeded to uninstall selinux.  I appears the selinux on Ubuntu is hosed, and after much dubbing around with this, I decided to install the latest selinux packages from the [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) ( I used Lenny in order to get the next highest version over the Ubuntu version). I installed anything that had to do with selinux.  Below is a list of files that I used:

libselinux1_2.0.65-5_amd64.deb
libsemanage1_2.0.25-2_amd64.deb
libsetools-tcl_3.3.5.ds-5_amd64.deb
policycoreutils_2.0.49-6_amd64.deb
python-selinux_2.0.65-5_amd64.deb
python-semanage_2.0.25-2_amd64.deb
python-sepolgen_1.0.11-5_all.deb
selinux-basics_0.3.5_all.deb
selinux-doc_1.26-1_all.deb
selinux-policy-default_0.0.20080702-6_all.deb
selinux-policy-doc_0.0.20080702-6_all.deb
selinux-policy-mls_0.0.20080702-6_all.deb
selinux-policy-refpolicy-doc_0.0.20061018-5.1+etch1_all.deb
selinux-policy-refpolicy-targeted_0.0.20061018-5.1+etch1_all.deb
selinux-policy-src_0.0.20080702-6_all.deb
setools_3.3.5.ds-5_amd64.deb

Lastly, I had to change the init program from upstart-compat-sysv to sysvinit to be able to boot selinux

sudo apt-get install sysvinit

Nothing seems to ever go that smooth.  After installing sysvinit, I could not gracefully reboot.  It would just go back to the login screen.  Luckily, I had sysrqd installed, which I allowed me to gracefully sync and unmount the RAID hard drives, then reboot.  If you want more info on sysrqd, google it with the "REISUB" keyboard sequence 


Note:  the audit2allow command from Ubuntu did not work because of the import python-sepolgen error.  The import statement should just be sepolgen.  Additionally, there was a problem with the python-selinux shared object file.  Updating all selinux packages cured this problem.  Hence, audit2allow command works fine after upgrade.

Hope this info helps!

---

### Post by bodhi.zazen on 2009-01-21
Thank you for the information [tgilber1]("http://ubuntuforums.org/member.php?u=454590")

To be honest, for all that effort, I would almost prefer to install from source or better use Fedora or Centos.

+1 on audit2allow

It is a really really nice tool.

---

### Post by uljanow on 2009-01-21
The default security framework in Ubuntu is AppArmor (developed by Novell) which is easier to configure.

---

