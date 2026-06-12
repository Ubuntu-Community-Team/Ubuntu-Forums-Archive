---
title: "Setting tty resolution in Ubuntu Server 13.10 within VMware"
date: 2013-11-04
forum: Server Platforms
---

### Post by allie2 on 2013-11-04
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=trebuchet ms]I've completed an install of Ubuntu Server 13.10 within VMware and am running into a problem configuring the console (non-graphical) resolution.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=trebuchet ms]When I was running Ubuntu Server 13.04, I ran into the same problem... [posted the question here]("http://askubuntu.com/questions/299975/proper-way-to-change-terminal-resolution-in-ubuntu-server-13-04"), which I later solved by editing /etc/default/grub thus:
[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=trebuchet ms]GRUB_CMDLINE_LINUX_DEFAULT="splash vga=789"
[/FONT][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=trebuchet ms]
I then ran sudo update-grub, sudo reboot and 13.04 stuck in a larger-size console mode... just what I wanted. BUT when I run the same commands in 13.10, during the reboot it changes to the new screen-res, BUT the screen stays black and I can't interact with it. I power down the VM, go back to a previous snapshot, and try again... and again.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=trebuchet ms]
Since the hwinfo package is no longer available in 13.10, I can't run sudo hwinfo --framebuffer to see what options are available.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=trebuchet ms]Here are the back-to-basics, un-commented settings in my /etc/default/grub file at this moment:
[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=trebuchet ms]GRUB_DEFAULT=0[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_HIDDEN_TIMEOUT=0[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_HIDDEN_TIMEOUT_QUIET=false[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_TIMEOUT=10[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_CMDLINE_LINUX_DEFAULT="splash"[/FONT][/SIZE]
[SIZE=2][FONT=trebuchet ms]GRUB_CMDLINE_LINUX="find_preseed=/preseed.cfg"

I've tried all kinds of solutions found online, have run 'sudo update-grub' and 'sudo reboot' after each one. None have worked and many have changed the console-size, but left me with a blank-black screen. Fortunately, I saved VMware snapshots after each change that did not leave me with a blank-black screen, so I was able to backtrack.

At this moment, I'm frustrated and need some expert help.[/FONT][/SIZE]

---

### Post by sudodus on 2013-11-04
Welcome to the Ubuntu Forums :-)

Can you try according to this link (run ***vbeinfo*** when in the grub menu) to get the available resolutions?[URL="http://askubuntu.com/questions/103516/grub2-use-maximum-detected-resolution"]

http://askubuntu.com/questions/103516/grub2-use-maximum-detected-resolution[/URL]

---

### Post by allie2 on 2013-11-05
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Can you try according to this link (run ***vbeinfo*** when in the grub menu) to get the available resolutions?[URL="http://askubuntu.com/questions/103516/grub2-use-maximum-detected-resolution"]

http://askubuntu.com/questions/103516/grub2-use-maximum-detected-resolution[/URL]

Yes. I've run vbeinfo from the grub command-prompt. In my case, I'm running Ubuntu Server within VMware Workstation AND I'm interested in 800x600 and vbeinfo shows that 800x600x32 is available. So, I edit /etc/default/grub thus

GRUB_GFXMODE=800x600

save it, run 'sudo update-grub' and 'sudo reboot'. The Grub portion of the loader changes to 800x600, but quickly reverts to 640x480 as Ubuntu Server starts up. This worked with Ubuntu Server 13.04, but doesn't with 13.10.

---

### Post by sudodus on 2013-11-06
I see. Have you tried with the full specification

GRUB_GFXMODE=800x600x32

If that does not work, it is a regression or bug (that I was not aware of).

Is it necessary to run Ubuntu Server version 13.10? The version 12.04.3 LTS is well debugged and polished, and has support until April 2017. The long time support versions are recommended for professional use (companies, organisations, and also the production system of private persons). The only exception is if some hardware or necessary software package is too new to run well with an ageing LTS version.

The next LTS version will be 14.04 to be released in April 2014, and you can expect that it will be possible to upgrade directly from one LTS system to the next one in July or August, at the first point release (so from an updated/dist-upgraded 12.04 to 14.04.1).

---

### Post by allie2 on 2013-11-06
> **sudodus said:**
> I see. Have you tried with the full specification

GRUB_GFXMODE=800x600x32

If that does not work, it is a regression or bug (that I was not aware of).

I just tried the full specification of GRUB_GFXMODE=800x600x32 and no problem-resolution (no pun intended).

> **sudodus said:**
> Is it necessary to run Ubuntu Server version 13.10? The version 12.04.3 LTS is well debugged and polished, and has support until April 2017.

No, not necessary to v13.10, so I'll take your suggestion and fall back onto 12.04 LTS. You're right, 12.04 LTS is more polished and debugged, so will stick with what's "safe and working".

Thanks, *sudodus*, for your help and input.

---

### Post by sudodus on 2013-11-06
You are welcome :-)

When/if you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by allie2 on 2013-11-06
> **sudodus said:**
> You are welcome :-)

When/if you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

Hmmm, moving from Ubuntu Server 13.10 back to 12.04 is *a solution of sorts*, but it *doesn't resolve the problem* of setting console/tty resolution when set up in VMware Workstation.

Think I'll leave this thread open for a while, to see if anyone else has other ideas.

---

### Post by JoarJ on 2013-12-25
I've got an Nvidia card, and have been using this solution for the last 3-4 years: [http://cosmicb.no/2013/12/25/ubuntu-13-10-console-resolution/](http://cosmicb.no/2013/12/25/ubuntu-13-10-console-resolution/)

---

