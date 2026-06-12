---
title: "how do you configure LXC so the container has sound"
date: 2013-11-07
forum: Virtualisation
---

### Post by bmullan2 on 2013-11-07
I've searched for a week for an example of how to configure this and there is really nothing that a google can find... other than myself and a few others asking "how to".

Does anyone know of a web page or a document that describes how to enable sound in an LXC container.

---

### Post by bmullan2 on 2013-11-09
I've read all the lxc-user mail back to April 2011 [URL="http://osdir.com/ml/lxc-chroot-linux-containers/2013-11/"]
http://osdir.com/ml/lxc-chroot-linux-containers/2013-11/[/URL]

and can't find any previous mail on the subject describing the steps involved:

[FONT=Lucida Grande][COLOR=#000000]I will admit that I may not be doing things right or may have left something out.  

I am using Ubuntu 13.10 and LXC.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
On the host I do the following:
**$ sudo mount &#8220;-o rw,bind&#8221; &#8220;/dev/snd&#8221; &#8220;/var/lib/lxc/CN_name/rootfs/dev/snd&#8221;**[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
I then edited the /var/lib/lxc/CN_name/config and added:
**lxc.cgroup.devices.allow = c 116:* rwm**[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
I then start the container CN_name ( $ sudo lxc-start -n CN_name)[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]after this I still cannot get any sound out of the container.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
I did a check:[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]$ lspci -v | more[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
and it comes back with Capabilities Denied for all PCI devices (re my hosts sound card) but again I am not LXC "smart" enough to know if that's the problem and if it is how to resolve it.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
Although I have seen multiple posts be people around the web saying it can be done or that they have done it there is never anything added as to describing the commands or /var/lib/lxc/cn_name/config entries required.[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]
I had really assumed that something like this would have been documented by now ... somewhere by someone.   [/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]The problem is NOT getting a gnome/unity/lxde/xfce etc desktop running in the container its that there's no sound present
[/COLOR]
Even Docker's Desktop:  
[http://blog.docker.io/2013/07/docker-desktop-your-desktop-over-ssh-running-inside-of-a-docker-container/#more-368](http://blog.docker.io/2013/07/docker-desktop-your-desktop-over-ssh-running-inside-of-a-docker-container/#more-368)  

Although presenting a Desktop via ssh to a container doesn't have sound (if you were to start firefox and go to youtube... no sound) 
I've check ubuntu, arch, debian, mint etc distro LXC documentation and there just is no documentation concerning the steps to do this ?[/FONT]

---

### Post by bmullan2 on 2013-11-10
[FONT=arial]I'd just sent in an email to the lxc-users list concerning Sound in an LXC container and what seemed [/FONT][FONT=arial]to me a lack of any good available information about how to configure it.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Well, last night I finally figured out what I had to do to make it work *after seeing a 1 line entry in a Debian oriented blogger's post* about LXC and some other device he was enabling in a container.[/FONT]
[FONT=arial]
***I did successfully finally get Sound to work from a desktop running in an LXC container in my Ubuntu 13.10 x64 system !***[/FONT]

[FONT=arial]One thing remains though is that PulseAudio "by default" in Ubuntu appears to be locked/owned by whichever Desktop grabs it first. [/FONT]

[FONT=arial]This would prevent multiple LXC container Desktops from all using Sound simultaneously/concurrently for multiple users.[/FONT]

[FONT=arial]However, _there is a solution,_ requiring a per-user pulseaudio config change that appears minimal that I've found but have not yet had time to implement and try.[/FONT]

[FONT=arial]As soon as I do, I will in a few days try to document what I've done so others interested in the same don't have to go through the same research.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]In the end my particular problem really boiled down to existing documentation being very minimal regarding this.

[/FONT]

---

