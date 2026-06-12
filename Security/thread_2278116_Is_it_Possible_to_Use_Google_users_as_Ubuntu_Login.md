---
title: "Is it Possible to Use Google users as Ubuntu Logins? (aka Google Domain Controller)"
date: 2015-05-14
forum: Security
---

### Post by fieroboom2 on 2015-05-14
[COLOR=#000000][FONT=Arial]Hello all. Before we all suck the air out of our rooms, gasping @ those last 3 words in the title[/FONT][/COLOR][COLOR=#000000][FONT=Arial], please read the whole post...  [/FONT][/COLOR];)
[COLOR=#000000][FONT=Arial]For those that might understand it immediately, here's the gist of what I want, with an explanation following:

**_Assumptions:_**
- Assume I am designing a 4-5 Edubuntu workstations to donate to the special education dept of my local public school.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]- Assume EVERY user of these workstations has a Google account.
- Assume that the users do NOT need to be created in Ubuntu, nor do they need any type of special session settings when they login (a single guest account is fine).
[U][B]
Desired Flow:[/B][/U]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]- User sits down to a an session login screen (Unity Greeter, etc).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- User enters their Google login credentials as if it's their Ubuntu login.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Ubuntu accepts, but assumes ANY greeter login is a single (and restricted) guest login. In other words, the entered credentials are irrelevant to the actual session login.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Ubuntu temporarily captures the credentials, and once login is complete, feeds those credentials to chrome, automatically logging said user into their Chrome/Google account.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Once user is finished & logs out, the session cleanup flushes the Chrome/Google credentials.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]_**&#8203;Explanation:**_
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]So here's my situation... I'm putting together 4-5 computers to donate to the special education department of my local public school. This department, although not completely independent of the overall school's network, does have a LOT of latitude in what the sysadmins will allow them to do, so I suggested that I could put together a few Edubuntu systems for them to try on some old(er) hardware I've got lying here, and they LOVED the idea, since they only have ONE workstation...  :([/FONT][/COLOR][COLOR=#000000][FONT=Arial]
Chrome (IMHO) is pretty awesome at bringing you all of your cloud storage/bookmarks/settings/email to any computer once you login to google or chrome, but let's face it: the design is geared toward a single user on their personal PC with the occasional "other user" login, and not multiple unique users constantly requiring login in & complete logout of google's apps... Plus there's the actual Chrome login within Chrome's settings that make it difficult to easily transition from user to user within the Chrome application itself...[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Does anyone have any idea how this might be accomplished?[/FONT][/COLOR][FONT=Arial][COLOR=#000000]
Due to the absolute ZERO information I've been able to dig up on this particular type of thing, I'm assuming the answer is a resounding "NO," but I thought I'd give it a try anyway...
The students definitely DO need their Chrome user logged in, but I'm attempting to avoid the logout forgetfulness, especially considering the students that will be using these stations.
In any case, thanks to all of you for reading, and thanks in advance for any assistance/suggestions you might have.   [/COLOR][/FONT]:p[FONT=Arial][COLOR=#000000]
[/COLOR][/FONT][FONT=Arial][COLOR=#000000]-Paul[/COLOR][/FONT]

---

### Post by TheFu on 2015-05-14
Sounds like you are seeking ChromeOS. [http://www.cnet.com/news/google-pushes-chrome-os-software-with-or-without-chromebooks/](http://www.cnet.com/news/google-pushes-chrome-os-software-with-or-without-chromebooks/) It doesn't do everything you want, but some crontab entries can probably handle the setup/cleanup, I suspect. Looked at section 5 crontab manpage hoping to find a @login or @logoff - after all they have an @reboot.  Didn't find anything. Perhaps if the ~/.logout forced a reboot, the cleanup could use an @reboot cron entry? Of course, every userid would need to be allowed to run /sbin/reboot in the sudoers file.

Interesting problem.

Do you care if **anyone** (non-students too) walks up and uses the equipment with their google account(s)?

Anyway - just a thought.  I have a chromebook, but only ran chromeos long enough to switch to legacy boot mode then immediately wiped the OS and instlled what I wanted.

---

### Post by fieroboom2 on 2015-05-14
TheFu, thanks so much for your input; I'll certainly have a look at your suggestions.
To answer your question, no I don't care if **anyone** uses it, because Ubuntu would assume that ANY greeter login is "guest" with restricted access.
In addition, I'm currently testing 3 different types/methods of system setup:
[LIST]
[*]Preconfigured LiveCD running from a flash drive
[LIST]
[*]Pro: I have TONS of old 2-16GB flash drives 
[*]Pro: Should the system crash for any reason, the instructor can simply power down, replace with a "new" flash drive, & return the defective ones to me for reconfig/disposal/etc. 
[*]Pro: Invulnerability.
[LIST]
[*]Still allows downloads, installations, etc that won't persist across reboots thanks to the RAM disk nature of a LiveCD. 
[*]Theft & physical damage of the HW pose no threat to loss/retreival of sensitive information. 
[*]I don't think even rm -rf nor partitioning/formatting will work, since the OS sees itself as a LiveCD mounted RO... ( haven't tested) 
[/LIST]
  
[*]Pro: Very little support intervention required once flash drives are configured 
[*]Con: Requires more RAM. Once the memory size threshold is reached, system locks until something crashes (and Chrome STILL likes to eat a LOT of memory...) 
[*]Con: ....?  (Input Welcomed) 
[/LIST]
  
[*]OS fully installed to the hard drive then once setup/configuration is complete, HDD is mounted RO
[LIST]
[*]Pro: No need to mess with bunches-o-flash drives 
[*]Pro: Still fairly invulnerable, unless a user figures out how to enter Recovery Mode & drop to a root prompt, then mess stuff up (highly unlikely, considering the pool of users). 
[*]Con: Support intervention required more often when something "ain't werkin." A system crash would be down until *I* was able to come repair it. 
[*]Con: Same RAM limitaions as above 
[*]Again, input is welcomed 
[/LIST]
  
[*]Full-out LTSP server with thin clients
[LIST]
[*]Pro: Again, stations are mostly invulnerable. Server is more vulnerable, but again, considering the pool of regular users, I feel it's negligible. 
[*]Pro: If workstation crashes for any reason, simply replace it with another PXE configured machine 
[*]Con: If the server crashes, ALL stations go down 
[*]Con: Most likely will require the most support intervention of the 3 
[*]PossibleCon: I'm uncertain if I have hardware powerful enough to run an LTSP server serving 4-5 clients 
[/LIST]
  
[/LIST]

Anyway, sorry for the novel, but that's the general idea. I'm aware there are MANY more details, pros, cons, etc, but from testing done to date, the LiveCD on flash drive seems best suited here (actual CDs have inherently slower access times).

Thanks again for your input; I'm looking into ChromeOS now.  :p

---

### Post by TheFu on 2015-05-14
CD and Flash drives are slow.  I'm willing to use them only long enough to get something useful installed.  If you go that route, let the kids provide their own flash drives and distros.

If you need something light - check out TinyCorePlus.  IBM uses it for special use deployments like this and it loads into RAM since it is so small. Launching programs is nearly instantaneous.  No login needed - so users would need to use their google credentials in the normal way.  I use this distro as my online banking boot distro - single purpose from a read-only VM ISO. For cloud-only users, tinycore or tinycoreplus are what I'd do (make the networking work automatically).  One of the core developers for that group is in my LUG, so I may be able to get more help if you need it.

None of the options you've listed seem too bad.

---

### Post by fieroboom2 on 2015-05-15
> **TheFu said:**
> If you need something light - check out TinyCorePlus.None of the options you've listed seem too bad.

I looked at TinyCore, and it reminds me of DSL... Extremely functional for people like us, but not quite as "pretty" as mainstream Ubuntu.
And yes, I realize I must decide where to make my compromise, but I'm running 14.04.1 on a Dell Vostro 1500 that does fine:
```
root@vostro:~# cat /proc/meminfo |head -n2
MemTotal:        2048520 kB
MemFree:          335660 kB


root@vostro:~# lshw -C processor
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       slot: Microprocessor
       size: 1401MHz
       capacity: 1401MHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm cpufreq
       configuration: cores=2 enabledcores=2 threads=2

```

Most of the hardware I have is about this equivalent in terms of performance, so I don't need anything sooper lightweight... Although I recently tested Lubuntu 14.04, and I really like it. On this older hardware, it's smooth, "pretty," and fast.

I started pondering all the Ubuntu media servers people have built, and realized if XBMC can be made a frontend, then I could possibly build a customized session login that launches Chrome. Also, Chrome has a few plugins, etc to force logout (Ephemeral mode), etc, so I might be able to hack something together without too much scripting, lol.

Resources:
[http://ubuntuforums.org/showthread.php?t=2203100](http://ubuntuforums.org/showthread.php?t=2203100)
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)
[https://support.google.com/chrome/a/answer/3538894](https://support.google.com/chrome/a/answer/3538894)

---

### Post by TheFu on 2015-05-15
XBMC is dead and not really what you want.  Kodi is the replacment - still not what you want. I boot into a Kodi session myself (on my HTPC) - nothing special about that. You can load any program you like in the same way.

How did chromeOS work out? That is still my best suggestion.

Also - it isn't too hard to customize tinycore-whatever as you like.  Load network drivers and settings, have a user login, don't allow saving anything local, etc.  The smaller platform also makes it much less useful if hacked.

Besides these things, I haven't any further ideas. Sorry.

---

