---
title: "panp8 questions"
date: 2011-07-27
forum: System76 Support
---

### Post by gdgilda on 2011-07-27
Hello,

I recently ordered and received a panp8.  Overall I've been quite happy with the system and was also happy to receive it nearly a week ahead of the originally projected arrival date.  Kudos to the system76 team!

I have two issues that I'd like to ask about here.  Before I get into the issues, here's information on my system configuration:
panp8
i5-2410M Processor
4 GB Dual Channel DDR3 SDRAM at 1333MHz
320 GB 7200 RPM SATA II
ubuntu 11.04 64b (as configured from factory)

First issue:
I twice ran into a situation where the keyboard froze when editting a libreoffice spreadsheet in with the window maximized.  The mouse moved but clicking had no effect, and no keyboard input was accepted, including alt-ctl-F5 or alt-ctl-del.  I had to turn off power and reboot.  The specific action that I was doing both times was to copy and paste a pair of columns in the spreadsheet into a pair of empty columns.  The 3rd time, I tried the same actions without having the window maximized and no keyboard freeze occurred (coincidence?).
I looked in the syslogs when this occurred and did not see anything in the log near the time when this happened.  I did notice the following message in syslog but it was at least a half hour before the keyboard freeze, so I don't think it's related:
Jul 24 16:34:52 redbird kernel: [   43.523916] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 9147, at 9147], missed IRQ?
Has anyone else seen an issue like this?  I can try recreating and capturing more information if that would help.

Second issue:
I'm not sure this is really an issue, but something I noticed when going through the logs for the first issue.  As background, when I went through the initial ubuntu configuration, I selected to have my home encrypted.
The message that I'm seeing in syslog is:
Jul 27 10:46:59 redbird modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.38-10-generic/kernel/drivers/crypto/padlock-sha.ko): No such device

I'm thinking a FATAL error is probably not a good thing, but would like some feedback on whether or not I should be concerned.  I've noticed that some of my gz'ed syslogs don't seem to have this error, so it seems to have been introduced sometime after I did the initial configuration, perhaps when I did a system update a few days and reboots later.

Log.tar is attached.  Thanks for any help you can provide.

Glenn

---

### Post by isantop on 2011-08-01
The second, "fatal" error is actually completely benign, as it refers to a hardware encryption chip. Ubuntu is trying to load it for people with the chip, and failing since it can't find it.

As for the second problem, was the window in fullscreen or just maximized?

---

### Post by gdgilda on 2011-08-05
> **isantop said:**
> The second, "fatal" error is actually completely benign, as it refers to a hardware encryption chip. Ubuntu is trying to load it for people with the chip, and failing since it can't find it.

As for the second problem, was the window in fullscreen or just maximized?
Thanks for the reply!  Regarding the 1st problem with the libreoffice keyboard hang, I had previously maximized the window using the maximize button on the upper left of the window.

I'll try to reproduce the problem again when I have a bit of time to look into it some more and will post more details if I can recreate.

Glenn

---

### Post by gdgilda on 2011-08-06
> **isantop said:**
> The second, "fatal" error is actually completely benign, as it refers to a hardware encryption chip. Ubuntu is trying to load it for people with the chip, and failing since it can't find it.

As for the second problem, was the window in fullscreen or just maximized?

Per my earlier reply, I spent some more time recreating the keyboard hang problem using libreoffice.  It is actually very easy to recreate.  I simply open a blank spreadsheet, either maximized or not, and select a couple of columns by left-clicking on a column label at the top (e.g. column B) and then shift-left clicking on the next column over (e.g. column C).  Doing a Control-C at that point to select the columns for copying does the trick and the keyboard is then hung.

One odd thing that I noticed is that as I reported before, trying to switch to a login prompt using alt-ctl-F5 doesn't work.  However, if I decide to wait for a bit, the fan kicks on and then alt-ctrl-F5 works.  I can even switch back to the window session using alt-ctl-F7 but the keyboard and mouse clicks are still nonfunctional in that session.

While back in the terminal session, I did a 'tail syslog >faillog', the results of which are shown here:
Aug  6 22:38:48 redbird NetworkManager[831]: <info> Activation (wlan0) successful, device activated.
Aug  6 22:38:48 redbird NetworkManager[831]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  6 22:38:56 redbird kernel: [   47.742823] wlan0: no IPv6 routers present
Aug  6 22:38:56 redbird ntpdate[1643]: adjust time server 91.189.94.4 offset -0.168642 sec
Aug  6 22:40:27 redbird kernel: [  138.581372] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Aug  6 22:40:27 redbird kernel: [  138.584012] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 45659 at 45651, next 45660)
Aug  6 22:40:51 redbird acpid: client 977[0:0] has disconnected
Aug  6 22:40:51 redbird acpid: client connected from 977[0:0]
Aug  6 22:40:51 redbird acpid: 1 client rule loaded
Aug  6 22:40:51 redbird kernel: [  163.040783] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

The GPU hung message seems to occur about the time when I recreate the keyboard hang.

Please let me know if you need more information.

Thanks,
Glenn

---

### Post by gdgilda on 2011-08-12
Hello,

I searched through the ubuntu general help forum for calc hangs and found others seemed to be having similar problems, not only on ubuntu 11.04 but on mint as well.  I tried one of the sugggested workarounds (turn off anti-aliasing under tools->options in calc) and that did fix the problem in calc.  Later during the same session, however, after I was done using calc and was reading this forum in firefox, I had a complete system freeze.  Coincidence?

Comments in some of the other threads have indicated a possible bug with sandybridge support.  Is there a bug opened yet?

Thanks,
Glenn

---

### Post by isantop on 2011-08-18
We haven't seen any widespread issues with Sandy Bridge yet. I think the freeze in Firefox was a coincidence, so I'd keep an eye on it, and let us know if there are any other problems or more freezes.

---

### Post by gdgilda on 2011-08-18
Thanks for your reply.  Are you able to recreate this problem on a panp8?  It is very repeatable for me as I described in my post from a week ago which included the procedure I used to recreate.  I do have a workaround (turn off anti-aliasing in libreoffice calc) but would like to know if the cause is understood or being investigated.  I rather suspect this is not a panp8 problem per se, so am willing to post this elsewhere if you have a suggestion.

Thanks,
Glenn

---

### Post by isantop on 2011-08-19
I have been able to reproduce your issue on a PanP8, but only in Libreoffice. Have you had any other consistent crashes with any other programs? 

My guess is that the problem is due to the driver used for the Sandy Bridge GPU. There will be an all new driver version present in Oneiric, so it should be fixed then.

---

### Post by gdgilda on 2011-08-19
Hi,

No, I've only seen a consistent problem in libreoffice.  I saw a hang once in firefox but that was only once and after I had just been doing something in calc.

The workaround (turning off anti-aliasing in libreoffice) seems pretty solid since I was working on a spreadsheet for a couple of hours tonight and adding rows and columns without any hang.

I'll look forward to trying out that new driver when it arrives in oneric, thanks for the update!

Glenn

---

