---
title: "Tips on maintaining a computer for a senior citizen?"
date: 2017-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-05-27
I've installed Lubuntu 16.04 on my dad's old Dell Inspiron E1505.

My dad isn't really a computer literate, all he knows about computer is using Facebook and playing his Candy Crush Saga, which is a game found in Facebook, so when it comes to updating and clicking the update when it comes up, he doesn't know what to do, he usually ignores them.

So, how do I automate things for him? Because there will be times when I'm away and I don't want to get a phone call that my dad's laptop was ransomwared because of outdated software.

---

### Post by yancek on 2017-05-27
The link below is the official Ubuntu documentation on auto updates with 16.04.

[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)

---

### Post by ian-weisser on 2017-05-27
I've done this for a few older family members. Some remote, some local.

It's worked out best by putting their stuff into online services (Gmail, Facebook, Picasa, etc). All they need is a web browser. They have used web browsers for 20 years - no surprises there.
I uninstall just about everything else.

I usually make two customizations.
1) I uninstall update-notifier and software-updater and software center. I edit unattended-upgrades to handle all updates automatically in the background.
2) I install a VNC server for reverse-VNC connections, so I can see their desktop remotely, if needed. It comes up maybe every to or three years. The server is NOT running, it's just installed. When they get me on the phone, I give them the shell incantations to safely share their desktop with me.

I find that their hardware usually wears out before the LTS needs to be release-upgraded. Some of these folks are online way more than me.
I have one relative who keeps managing to corrupt her OS somehow, but she's perfectly happy to drop by for a visit while I reinstall it for her. It's an excuse for her to share her award-winning tea-bread. Yum! Everybody wins!

I don't install any backdoors or SSH servers on their system. No need.

---

### Post by ardouronerous on 2017-05-27
Thanks for the replies.
On VNC server, I'm not sure my dad will agree to that, because he takes pride in his privacy, so for me to see their desktop remotely is something he'd not agree with, and so I don't want to violate his privacy and beliefs.

On the unattended-upgrades, just for confirmation, so I install it via terminal:

```
 sudo apt install unattended-upgrades
```

then I edit /etc/apt/apt.conf.d/50unattended-upgrades and add these:

```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu xenial-security";
//      "Ubuntu xenial-updates";
};
```

This will autoupdate all software in Lubuntu?

What kind of behavior should I expect from unattended updates? Because I've never done autoupdate before.

---

### Post by ardouronerous on 2017-05-28
Okay, I've installed unattended-upgrades, but now I'm at a loss on what  to do, here's the content of /etc/apt/apt.conf.d/50unattended-upgrades:

```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    // Extended Security Maintenance; doesn't necessarily exist for
    // every release and this system may not have it installed, but if
    // available, the policy for updates is such that unattended-upgrades
    // should also install from here by default.
    "${distro_id}ESM:${distro_codename}";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//    "vim";
//    "libc6";
//    "libc6-dev";
//    "libc6-i686";
};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";
```

I'm not exactly sure what to type or edit in this file.

---

### Post by HermanAB on 2017-05-28
Ayup - use an LTS version and disable updates.  The machine will likely keep running for a decade or more with zero maintenance.

I had servers on the wild wild web running 24/7 for more than 4 years at a stretch with zero maintenance and zero reboots - eventually the PSUs fail.

However, do them a favour and provide a very high resolution large screen.  Elderly people's biggest problem is failing eyesight.   A huge screen with umpteen bazillion pixels go a long way to fix that problem.

Finally, bear in mind that elderly people are typically not much interested in advertisements - they already have everything they need.  You can get a good /etc/hosts file to efficiently squash and square the rubbish on the wild wild web here:
[https://github.com/StevenBlack/hosts](https://github.com/StevenBlack/hosts)

---

### Post by ian-weisser on 2017-05-28
> **ardouronerous said:**
> On VNC server, I'm not sure my dad will agree to that, because he takes pride in his privacy, so for me to see their desktop remotely is something he'd not agree with, and so I don't want to violate his privacy and beliefs.

Well, that's an easy answer then. If he doesn't want it, don't do it.



> **ardouronerous said:**
> 
```
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu xenial-security";
//      "Ubuntu xenial-updates";
};
```

This will autoupdate all software in Lubuntu?

It will provide security updates, which is all you really want. This is a good answer.
Other updates may, annoyingly, change layouts or settings or software choices...without enhancing security. Great for others, but unlikely to be helpful for your use case.
HermanAB's answer is a bit different, and also appropriate.



> **ardouronerous said:**
> What kind of behavior should I expect from unattended updates? Because I've never done autoupdate before.
You should expect no user-detectable behavior at all. That's what 'unattended' means.
Of course, vulnerability to malware should also be --silently-- markedly reduced.
No prompts to update. No reminders to update. No warnings that you're not updated. Totally unattended.

One common question is 'How can I tell that Unattended-Upgrades is running?

There are two easy ways to tell:
1) Check the timestamp file for the last successful run (**  ls -l /var/lib/apt/periodic **)
2) Check the log file ( **less /var/log/unattended-upgrades/unattended-upgrades.log** )



> **ardouronerous said:**
> Okay, I've installed unattended-upgrades, but now I'm at a loss on what  to do, here's the content of /etc/apt/apt.conf.d/50unattended-upgrades:
The default settings are a good place to start.
Change nothing until you know what you want to change and why.


HermanAB's excellent advice shows that it's a rich tapestry. Pick and choose the features you want.
You probably won't hit on a perfect solution on the first try. People are complicated.
Happily, you can iterate toward better each time you see the person.

---

### Post by ardouronerous on 2017-05-28
Okay thanks for the advice! :)

> **ian-weisser said:**
>  HermanAB's answer is a bit different, and also appropriate.

On HermanAB's advice, isn't it that disabling updates a bad idea on the Internet? That's what we were taught in computer class, to always keep software up to date because hackers can exploit outdated and unpatched software.

How long is Lubuntu 16.04 LTS supported?

> **ian-weisser said:**
> It will provide security updates, which is all you really want. This is a good answer.
Other updates may, annoyingly, change layouts or settings or software choices...without enhancing security. Great for others, but unlikely to be helpful for your use case.

Okay, will this also update software like Firefox, Chromium and Adobe Flash Player?

He uses Firefox and Adobe Flash Player for Facebook and to run his Candy Crush Sage game and he uses Chromium for Skype for Web.

---

### Post by vasa1 on 2017-05-28
> **ardouronerous said:**
> ...
Okay, will this also update software like Firefox, Chromium and Adobe Flash Player?

He uses Firefox and Adobe Flash Player for Facebook and to run his Candy Crush Sage game and he uses Chromium for Skype for Web.Yes.

---

### Post by ardouronerous on 2017-05-29
> **vasa1 said:**
> Yes.


Okay, thanks.


> **ian-weisser said:**
> You should expect no user-detectable behavior at all. That's what 'unattended' means.
Of course, vulnerability to malware should also be --silently-- markedly reduced.
No prompts to update. No reminders to update. No warnings that you're not updated. Totally unattended.


One common question is 'How can I tell that Unattended-Upgrades is running?


There are two easy ways to tell:
1) Check the timestamp file for the last successful run ( ls -l /var/lib/apt/periodic )
2) Check the log file ( less /var/log/unattended-upgrades/unattended-upgrades.log )


The default settings are a good place to start.
Change nothing until you know what you want to change and why.


Thanks for the info, but what about updates that require the user restart the PC, will there be prompts for restart?

---

### Post by mastablasta on 2017-05-29
> **HermanAB said:**
> Ayup - use an LTS version and disable updates.  The machine will likely keep running for a decade or more with zero maintenance.

I had servers on the wild wild web running 24/7 for more than 4 years at a stretch with zero maintenance and zero reboots - eventually the PSUs fail.


1. the topic is desktop where users actively surf on the web and deal with various java and flash exploits as well as browser exploits. all OS independent.
2. i did update server app (wordpress) fairly regulary. server was kept up to date by host. the problem was they still hacked it through a wordpress plugin that was deactivated and they hacked it 2 days after vulnerability was described and about 1 day before i would update it all.
3. you obviously got very lucky or didn't have many services requiring access. for example the SSH i am running get's at least 5 break in attempts per day. luckilly until now it was mostly scripted probes. 

> **ardouronerous said:**
> 

Thanks for the info, but what about updates that require the user restart the PC, will there be prompts for restart?

it should. but you can also schedule it (e.g. if PC is on all the time). check the config file:

```
// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";


// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

```

i also installed sendmail and set it up to use gmail account to send me an email about a succesfull update.

the "//" is comment, so to make a line work you just delete these. then you setup the line as you want.

---

### Post by mörgæs on 2017-05-29
> **ardouronerous said:**
> 
On HermanAB's advice, isn't it that disabling updates a bad idea on the Internet? That's what we were taught in computer class, to always keep software up to date because hackers can exploit outdated and unpatched software.

It most certainly is a bad idea and I don't understand that the moderators haven't edited the post. People who don't know better might be led astray. 

Always apply security updates, no exceptions from that rule. 

Maybe the whole problem could be solved if your dad learned to recognise the update button and push it any time it appears :-)

---

### Post by RobGoss on 2017-05-29
>  Thanks for the info, but what about updates that require the user restart the PC, will there be prompts for restart?   

The answer is yes the machine will require a restart for most updates so it's a good idea to show him how to apply it

I think it's a good idea to teach him how to update his system it would be better all the way around and is not hard at all. As long as he does not have to configure anything it should be OK

I know it harder on some seniors citizens but they're smarter then we may think

---

### Post by ardouronerous on 2017-05-29
> **mörgæs said:**
> It most certainly is a bad idea and I don't understand that the moderators haven't edited the post. People who don't know better might be led astray.

Always apply security updates, no exceptions from that rule.

I wasn't going to follow that advice because our computer teacher taught us to apply updates whenever they arise.

> **mörgæs said:**
> Maybe the whole problem could be solved if your dad learned to recognise the update button and push it any time it appears 
> **RobGoss said:**
> I think it's a good idea to teach him how to update his system it would be better all the way around and is not hard at all. As long as he does not have to configure anything it should be OK

I know it harder on some seniors citizens but they're smarter then we may think

Easier said than done in my case.

Can the update window appear during Firefox's fullscreen mode? My dad's eyesight is slightly bad and so Firefox's zoom is on 150% and the font is on 16 and is on fullscreen mode.

> **RobGoss said:**
> The answer is yes the machine will require a restart for most updates so it's a good idea to show him how to apply it

I heard that Ubuntu is developing a way so that updates need not require restarts, is that true?

---

### Post by RobGoss on 2017-05-29
> I heard that Ubuntu is developing a way so that updates need not require restarts, is that true?  

I haven't heard anything about this as of yet, I know it harder on some older folks 

> Can the update window appear during Firefox's fullscreen mode? My dad's eyesight is slightly bad and so Firefox's zoom is on 150% and the font is on 16 and is on fullscreen mode 

I don't use Firefox so I could not confirm this, The updater usually appears inn the right corner of the desktop and should still do this while in full screen mode using Firefox, at least I would think so

---

### Post by ardouronerous on 2017-05-29
> **RobGoss said:**
> I haven't heard anything about this as of yet, I know it harder on some older folks 

I think it's called livepatching I think.

> **RobGoss said:**
> I don't use Firefox so I could no confirm this, The updater usually appears inn the right corner of the desktop and should still do this while in full screen mode using Firefox, at least I would think so

During fullscreen mode, the desktop panel is hidden.

---

### Post by RobGoss on 2017-05-29
I'm using 16.04 and when updates are presented I get a dialog popup in the center of my desktop giving me the option to install them or do it later

---

### Post by SeijiSensei on 2017-05-29
> **ardouronerous said:**
> I heard that Ubuntu is developing a way so that updates need not require restarts, is that true?
Reboots are mostly required when the kernel is changed.  I don't see how they can be avoided since without a reboot the current vulnerable kernel would remain in operation.

Just be glad that reboots are so uncommon in the Linux updating process unlike *cough* Windows.

BTW, as a "senior citizen" myself, I don't think we have any unusual maintenance requirements beyond periodic updates.  I'm sure there are lots of sixteen-year-olds who aren't interested in maintaining their computers any more than your dad, and for whom the same suggestions would apply.

---

### Post by deadflowr on 2017-05-29
> Reboots are mostly required when the kernel is changed. I don't see how they can be avoided since without a reboot the current vulnerable kernel would remain in operation.
This is what the OP has heard mumblings about:
[https://www.ubuntu.com/server/livepatch]("https://www.ubuntu.com/server/livepatch")
Note that when they say it supports 16.04 and 14.04, it means the 4.4 kernel series, which is installable on 14.04 as the linux-blah-lts-xenial package(s) replace blah with whatever is appropriate; image,headers,generic.

---

### Post by RobGoss on 2017-05-29
I for one don't understand how some users will keep their machines updated, if they only knew how simple and important it is

---

### Post by ian-weisser on 2017-05-29
> **ardouronerous said:**
> Thanks for the info, but what about updates that require the user restart the PC, will there be prompts for restart?

Reboot prompts are, if I recall correctly, provided by the update-notifier package.
I remove that package...but that's mere personal preference.

If the user in question --like many-- shuts down the machine regularly, then the question is moot. The system will be restarted regardless of notice or need, so prompting the user seems unnecessary.

If the user does not restart their computer regularly, then unattended-updates has a setting to restart whenever required (including after a delay).
The option is turned off by default - you must simply turn it on and set the delay.
Both settings are in the settings file that you already know: /etc/apt/apt.conf.d/50unattended-upgrades
Prompting the user in this case also seems unnecessary.

If the user want to be prompted, then leave update-notifier installed.

---

### Post by vasa1 on 2017-05-29
And ask the user to sign up at Ubuntu Forums ;)

---

### Post by SeijiSensei on 2017-05-29
> **deadflowr said:**
> This is what the OP has heard mumblings about:
[https://www.ubuntu.com/server/livepatch]("https://www.ubuntu.com/server/livepatch")

I spent a couple minutes vainly searching for an explanation of how this technology works. Does it unload an existing kernel module and replaces it with the new one?  What if the change has to be made to the kernel's core?  Wouldn't that require a reboot?

---

### Post by mastablasta on 2017-05-30
> **RobGoss said:**
> I'm using 16.04 and when updates are presented I get a dialog popup in the center of my desktop giving me the option to install them or do it later

interesting. in KDE (at least the older one in 14.04) the update doesn't pop up. an icon appears in the taskbar and one has to click it to do the update (not sure what happens if they are on auto). then when they ar edone again small icon appears in taskbar. when clicking it it offers a reboot. 


i dont' like autoupdates on desktop as they interfere with work. i prefer to see that they are available and then i would run them.

---

### Post by ardouronerous on 2017-05-30
> **mastablasta said:**
> interesting. in KDE (at least the older one in 14.04) the update doesn't pop up. an icon appears in the taskbar and one has to click it to do the update (not sure what happens if they are on auto). then when they ar edone again small icon appears in taskbar. when clicking it it offers a reboot.

i dont' like autoupdates on desktop as they interfere with work. i prefer to see that they are available and then i would run them.

Unfortunately my dad would usually ignore updates and continues on his game.

> **deadflowr said:**
> This is what the OP has heard mumblings about:
[https://www.ubuntu.com/server/livepatch](https://www.ubuntu.com/server/livepatch)
Note that when they say it supports 16.04 and 14.04, it means the 4.4 kernel series, which is installable on 14.04 as the linux-blah-lts-xenial package(s) replace blah with whatever is appropriate; image,headers,generic.
> **SeijiSensei said:**
> I spent a couple minutes vainly searching for an explanation of how this technology works. Does it unload an existing kernel module and replaces it with the new one?  What if the change has to be made to the kernel's core?  Wouldn't that require a reboot?

I'm interested in what this has to offer. Based off what I've read, livepatching requires a Ubuntu One account and supports only up to three machines per user, well, I'm supporting two machines, my Xubuntu 16.04 desktop and my dad's Lubuntu 16.04 laptop.

Anyone has any experience with livepatching? Please share it here, thanks.

EDIT: Just read that livepatching only supports 64-bit, since my dad's laptop is circa 2007, it's 32-bit, too bad, I hope they'll support 32-bit in the future. 

How about system cleaning? Like Bleachbit? I use Bleachbit on my desktop to clean out the clutter from my surfing, is there anyway to automate this?

---

### Post by ardouronerous on 2017-05-30
> **ian-weisser said:**
> Reboot prompts are, if I recall correctly, provided by the update-notifier package.
I remove that package...but that's mere personal preference.

If the user in question --like many-- shuts down the machine regularly, then the question is moot. The system will be restarted regardless of notice or need, so prompting the user seems unnecessary.

If the user does not restart their computer regularly, then unattended-updates has a setting to restart whenever required (including after a delay).
The option is turned off by default - you must simply turn it on and set the delay.
Both settings are in the settings file that you already know: /etc/apt/apt.conf.d/50unattended-upgrades
Prompting the user in this case also seems unnecessary.

If the user want to be prompted, then leave update-notifier installed.

Yes my dad does shuts down the computer after usage, so it's okay for him to ignore restart prompts and just shut it down later?

---

### Post by SeijiSensei on 2017-05-30
> **ardouronerous said:**
> Yes my dad does shuts down the computer after usage, so it's okay for him to ignore restart prompts and just shut it down later?

Yes, and I would suggest you go this route.  Have the machine update itself automatically and rely on your father turning off the machine to handle the reboot issue.

---

### Post by pauljw on 2017-05-30
> **SeijiSensei said:**
> BTW, as a "senior citizen" myself, I don't think we have any unusual maintenance requirements beyond periodic updates.  I'm sure there are lots of sixteen-year-olds who aren't interested in maintaining their computers any more than your dad, and for whom the same suggestions would apply.

Thanks for that!  I was beginning to get a complex over all this "poor old senior citizen" talk.  :-)

---

### Post by ardouronerous on 2017-05-30
> **SeijiSensei said:**
> Yes, and I would suggest you go this route.   Have the machine update itself automatically and rely on your father  turning off the machine to handle the reboot issue.

Okay, thanks! :)

> **pauljw said:**
> Thanks for that! I was beginning to get a complex over all this "poor old senior citizen" talk. 

Well, if you know my dad, you'd know my dad never really grew up on computers, he only started using a computer on a daily basis when he was invited to Facebook almost 10 years ago, when he used to work as a manager for a company, it was his secretary that did most of his documents and emails, all he did was dictate it to her, and it was the IT guys in the company that maintained the computers, so for most of his adult life he never used a computer.

What about system cleaning? Is that necessary? Just like Ubuntu doesn't need defragging, does Lubuntu need to be cleaned or does it clean itself?

If the cache needs to be cleaned every so often, is there a way to automate it, like on startup?

---

### Post by lisati on 2017-05-30
> **ardouronerous said:**
> If the cache needs to be cleaned every so often, is there a way to automate it, like on startup?

Temporary files in /tmp are usually deleted automatically on startup.

---

### Post by ardouronerous on 2017-05-30
what about firefox's cache, cookies and history? and recently opened files, clipboard and such? Are those included in /tmp?

what about the files in /home/username/.cache? Are those cleaned on startup?

---

### Post by vasa1 on 2017-05-30
> **ardouronerous said:**
> what about firefox's cache, cookies and history? and recently opened files, clipboard and such? Are those included in /tmp?

what about the files in /home/username/.cache? Are those cleaned on startup?

I'm sure you can answer some of these questions yourself! :)

Why would you expect a browser's cache, cookies and history to be in tmp?

You can just open a file manager after a restart and look at the dates of files in ~/.cache.

---

### Post by ardouronerous on 2017-05-30
I just want to know, can I run Bleachbit on startup, not starting the program and it appears on startup, like automatically clean, because on Windows XP, I set CCleaner to clean on startup, can I do that with Bleachbit?

---

### Post by Geoffrey_Arndt on 2017-05-30
See below for how-to.   Startup programs including various agents and daemons have been running at startup in Unix since the 70's.  

[https://askubuntu.com/questions/895697/run-bleachbit-cli-at-startup](https://askubuntu.com/questions/895697/run-bleachbit-cli-at-startup)

---

### Post by SeijiSensei on 2017-05-30
What sorts of "cleaning" are we talking about here?  Is this a concern about running out of space on the disk drive?  Or is it some kind of obsession with privacy?  Who the hell is going to spend their time browsing your dad's Firefox cache?  If it's that big a deal, tell him to use a private browser window like Firefox supports.

Isn't Bleachbit a program that uses military-strength technologies to delete files and fill the space with zeroes?  Why on earth would he need anything like that?

There may be images hiding in my Firefox cache that might raise an eyebrow or two, but at 67 I could care less.

---

### Post by ardouronerous on 2017-05-30
> **SeijiSensei said:**
> What sorts of "cleaning" are we talking about here? Is this a concern about running out of space on the disk drive? Or is it some kind of obsession with privacy? Who the hell is going to spend their time browsing your dad's Firefox cache? If it's that big a deal, tell him to use a private browser window like Firefox supports.

Isn't Bleachbit a program that uses military-strength technologies to delete files and fill the space with zeroes? Why on earth would he need anything like that?

There may be images hiding in my Firefox cache that might raise an eyebrow or two, but at 67 I could care less.

Both actually, the hard drive of his laptop is only 120GB, and I cannot upgrade any higher, and yes, me and my dad are obsessed with privacy as I said from the start lol :)

I've been using Bleachbit since Xubuntu 12.04, didn't have any problems with it since I don't use root version of Bleachbit.

> **Geoffrey_Arndt said:**
> See below for how-to. Startup programs including various agents and daemons have been running at startup in Unix since the 70's.

[https://askubuntu.com/questions/895697/run-bleachbit-cli-at-startup](https://askubuntu.com/questions/895697/run-bleachbit-cli-at-startup)

Thanks for the info! :)

---

### Post by ardouronerous on 2017-05-31
Okay, that worked! :) 
I followed this:
[B]
Option 1: Editing the desktop configuration file manually[/B]

  When the *"Start BleachBit with computer"* checkbox is activated, it creates a desktop configuration file called bleachbit in ~/.config/autostart/. This is very well explained in the posts [Where are startup commands stored?]("https://askubuntu.com/q/63407/643185") and [URL="https://askubuntu.com/q/303694/643185"]where is “startup applications” user config file for disabled and enabled applications?
[/URL]
  [[IMG]https://i.stack.imgur.com/XFHoG.png[/IMG]]("https://i.stack.imgur.com/XFHoG.png")

  If you want to access the folder with nautilus make sure to enable *View > Show Hidden Files*, or use the Ctrl+H shortcut.
  
Edit the file with your text editor of choice, for example using gedit. Open the terminal and run the command:
  
```
gedit ~/.config/autostart/bleachbit
```
  
Inside the file, locate the line Exec=bleachbit and replace it with:
  
```
Exec=bleachbit -c --preset
```
  
Save the changes. We're done.
  
Notice that after saving, the desktop configuration file is renamed automatically to bleachbit.desktop. This is default behavior.

  [[IMG]https://i.stack.imgur.com/WyCiK.png[/IMG]]("https://i.stack.imgur.com/WyCiK.png")

---

### Post by SeijiSensei on 2017-05-31
I'm a lot more concerned about protecting my privacy while browsing the web.  That's why I use add-ons to Firefox like Ghostery.  

If your father is concerned about his privacy, why is he using Facebook?  That's a much bigger threat than the files stored in his browser cache.  Facebook has become a new source for phishing and other threats displacing email to a degree.  Even the [Defense Department was caught unawares]("https://www.nytimes.com/2017/05/28/technology/hackers-hide-cyberattacks-in-social-media-posts.html").

> Pentagon officials are increasingly worried that state-backed hackers are using social media sites such as Twitter and Facebook to break into Defense Department computer networks. And the human error that causes people to click on a link sent to them in an email is exponentially greater on social media sites, the officials said, because people are more likely consider themselves among friends.

And, of course, Facebook itself is [well-known]("https://www.forbes.com/sites/thomasbrewster/2016/06/29/facebook-location-tracking-friend-games/#685d1d1135f9") to play fast-and-loose with its members' information.

---

### Post by ardouronerous on 2017-05-31
Unfortunately, you cannot really escape Facebook, I mean you can choose not to use it, but still, unless you want to be a recluse? All my dad's friends are on Facebook, so he has no choice, unless he wants to disconnect from his friends.

I have Decentraleyes, Disconnect, Ghostery, NoScript, HTTPS Everywhere, Privacy Badger and uBlock Origin installed. Is that overkill though?

I also have Firefox's AppArmor profile and UFW enabled

---

### Post by SeijiSensei on 2017-06-01
I've never had a Facebook account and still have friends.

---

### Post by ardouronerous on 2017-06-01
To each his own then, personally, even though I do have a Facebook account because my relatives invited me, I barely visit it at all, I'm just not that interest in Facebook, I'd rather go to Wikipedia and read articles or watch Youtube videos than doing Facebook.

But again, to each his own, for my dad, Facebook provides him a good platform to find out what his friends are doing, and I do see his point, when compared to using email, Facebook's platform is indeed better.

---

### Post by mikodo on 2017-06-01
> **SeijiSensei said:**
> I've never had a Facebook account and still have friends.
This has been an informative thread. There are many good tips from multiple posters, I appreciate and plan to followup on. 

I wasn't going to post but, this made me laugh --- thanks, for that too!

---

### Post by gbartley1065 on 2017-06-01
Alternately you could use team viewer personal to connect to the computer to complete the maintenance.

---

### Post by vasa1 on 2017-06-01
> **gbartley1065 said:**
> Alternately you could use team viewer personal to connect to the computer to complete the maintenance.
See [https://ubuntuforums.org/showthread.php?t=2362553&p=13650110#post13650110](https://ubuntuforums.org/showthread.php?t=2362553&p=13650110#post13650110). Thanks.

---

### Post by ardouronerous on 2017-06-02
How do I make this cursor bigger?

Like I said, my dad's eyesight is bad, so when he was using Windows XP, there's an option to enlarge the cursor, is there an option in Lubuntu for that?

---

### Post by ardouronerous on 2017-06-03
I've found the solution on how to resize the cursor on Lubuntu, here's the instructions:

To change the size of your mouse cursor, go to:

```
/home/USERNAME/.config/lxsession/Lubuntu/desktop.conf
```

Find this line:

```
iGtk/CursorThemeSize=18
```

and change the value, in my case, my desired size is 36.

Then save and then do a reboot.

---

