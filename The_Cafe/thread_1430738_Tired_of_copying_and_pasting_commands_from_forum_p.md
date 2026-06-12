---
title: "Tired of copying and pasting commands from forum posts?"
date: 2010-03-15
forum: The Cafe
---

### Post by lovinglinux on 2010-03-15
Moved to [http://ubuntuforums.org/showthread.php?t=1543783](http://ubuntuforums.org/showthread.php?t=1543783)

---

### Post by kernelhaxor on 2010-03-15
Nice extension!

how about adding the 'Run in terminal' option to your extension? .. so I could get it all by just installing one add-on

---

### Post by Phrea on 2010-03-15
Wow, that's useful !!

Only problem is, I run Opera as default browser, but that might change [since it will not work properly on lin the way it should].

Great job, thanks. :popcorn:

---

### Post by lovinglinux on 2010-03-15
> **kernelhaxor said:**
> Nice extension!

how about adding the 'Run in terminal' option to your extension? .. so I could get it all by just installing one add-on

Thanks. I don't understand what you mean. You can run commands in terminal form the context menu, by simply selecting text on a page.


> **Phrea said:**
> Wow, that's useful !!

Only problem is, I run Opera as default browser, but that might change [since it will not work properly on lin the way it should].

Great job, thanks. :popcorn:

Thanks. I hope you go back to Firefox. It rocks :)

> **Bachstelze said:**
> Nice job. Have an Internets.

Thanks.

---

### Post by 2hot6ft2 on 2010-03-15
That looks promising. Nice work.

---

### Post by fatality_uk on 2010-03-15
Sweet!!

---

### Post by sudoer541 on 2010-03-15
> **lovinglinux said:**
> I have created a new Firefox extension to make the process of running commands from web sites a lot easier.

With [FoxRunner]("https://addons.mozilla.org/en-US/firefox/addon/98430") you can run shell commands from any web page through the context menu. Just select a command from a forum post or web article and run it. You can also save commands and scripts, then launch them through Firefox sidebar, context menu and status bar.

[Demo Video]("http://lovinglinux.megabyet.net/?p=495")  |  [Download & Info]("https://addons.mozilla.org/en-US/firefox/addon/98430")

[[IMG]http://img710.imageshack.us/img710/5772/foxrunner005.th.png[/IMG]]("http://img710.imageshack.us/img710/5772/foxrunner005.png")

Please test it and tell me what you think.

Also check [TerminalRun]("https://addons.mozilla.org/en-US/firefox/addon/9738") (not mine).


Great job!!!! I like it!!!

---

### Post by lovinglinux on 2010-03-15
Thanks. Any suggestion for improvement will be much appreciated.

---

### Post by ajgreeny on 2010-03-15
I always just highlight and then middle click in the open terminal when I need to run a command from a web page- as long as I know what it is all about and what it is both intended to do, and what it will actually do.  All it would save me is a single click on the terminal launcher on the panel.

I'm not suggesting the add-on is not worth all your effort, just that I don't think it is one for me to use.

Well done though;  many others seem to like the idea, and maybe I shall try it sometime and realise that it is worthwhile.

---

### Post by Shpongle on 2010-03-15
cool thats very useful , whats the music in the video ?

maybe a feature to open certain profiles for your shell , or different shells

---

### Post by lovinglinux on 2010-03-15
> **ajgreeny said:**
> I always just highlight and then middle click in the open terminal when I need to run a command from a web page- as long as I know what it is all about and what it is both intended to do, and what it will actually do.  All it would save me is a single click on the terminal launcher on the panel.

I'm not suggesting the add-on is not worth all your effort, just that I don't think it is one for me to use.

Well done though;  many others seem to like the idea, and maybe I shall try it sometime and realise that it is worthwhile.

That's just one of the features. You can also save commands and scripts and launch them from the status bar, context menu and sidebar. You can also use up to 10 variables on scripts and select those variables from a list before running a script.

> **DillByrne said:**
> cool thats very useful , whats the music in the video?

I don't remember the name. I got it from YouTube audio swap. The producer is MusicShake I guess.

> **DillByrne said:**
> cool thats very useful , whats the music in the video ?

maybe a feature to open certain profiles for your shell , or different shells

Thanks for the suggestion.

---

### Post by themarker0 on 2010-03-15
Are you making this addon for other browsers? I am trying to move away from the beast now :p

---

### Post by lovinglinux on 2010-03-15
> **themarker0 said:**
> Are you making this addon for other browsers? I am trying to move away from the beast now :p

Unfortunately no. I only do Firefox add-ons for now. Nevertheless, the code is released under GPL, so anyone is free to port it. I just don't have the skills and time.

---

### Post by DoktorSeven on 2010-03-15
I'm wondering if a page could be constructed to automatically run a malicious command with that extension installed...

but that's just the paranoid, security-crazy GNU/Linux guy in me. :)

---

### Post by swoll1980 on 2010-03-15
Good job! when I saw the thread title I thought it was a rant.

---

### Post by CharlesA on 2010-03-15
Oh awesome! Most of the time I am alt-tabbing and typing stuff out. >.<

---

### Post by themarker0 on 2010-03-15
> **lovinglinux said:**
> Unfortunately no. I only do Firefox add-ons for now. Nevertheless, the code is released under GPL, so anyone is free to port it. I just don't have the skills and time.

Then i'm sticking with FF then.

---

### Post by lovinglinux on 2010-03-16
> **DoktorSeven said:**
> I'm wondering if a page could be constructed to automatically run a malicious command with that extension installed...

but that's just the paranoid, security-crazy GNU/Linux guy in me. :)

EDITED:

Your are not paranoid. Those are concerns that crossed my mind too.
I have included in the latest version a permission functionality, that prevent running commands from unauthorized web sites. This is probably unnecessary, since the extension doesn't have any code that would allow a web site to start it's functions anyway. The extension works essentially by copying the command to the clipboard and parsing it to the terminal. Nevertheless, I'm providing this functionality as a "paranoid" mode and to avoid running commands accidentally. Additionally, I also included an option to request confirmation before running commands from sites and another option to request confirmation before running commands from the database. These confirmation dialogs also allow to choose if the command will be executed on a terminal or not. 

I also included a command blacklist functionality, that prevent commands containing certain keywords from running. You can add your own keywords to the list, but it comes already with some examples.

All these security layers can be disable/enabled in the extension preferences.

---

### Post by madjr on 2010-03-16
awesome

can you highlight a bunch of lines of text/commands and get them executed in 1 go ?

thx for the extension

---

### Post by wojox on 2010-03-16
Cool you just saved be some time flipping between windows. Good work. ;)

---

### Post by Keith1212 on 2010-03-16
I'm gonna try it for awhile thanks.

---

### Post by lovinglinux on 2010-03-16
> **madjr said:**
> awesome

can you highlight a bunch of lines of text/commands and get them executed in 1 go ?

thx for the extension

This works:

```
sudo apt-get update &&
sudo apt-get upgrade
```

This doesn't:

```
sudo apt-get update
sudo apt-get upgrade
```

I will try to improve this for the next version. Thanks for reminding me of this.

[TerminalRun](https://addons.mozilla.org/en-US/firefox/addon/9738) can do both.

---

### Post by Chame_Wizard on 2010-03-16
:o Damn good,so we have a winner.[IMG]http://i.fokzine.net/s/static.gif[/IMG]

---

### Post by lovinglinux on 2010-03-16
Thanks for all feedback. I'm glad with such positive comments.

I have included some notes about security and bugs on the first post.

---

### Post by ankspo71 on 2010-03-16
I really like this foxrunner addon. This is very convenient compared to launching the terminal, resizing windows, changing tabs, etc, just to run a simple set of commands.=D>

---

### Post by toupeiro on 2010-03-17
This could be very good, or *very* bad...  Historically speaking, running server-side code in userspace that invokes system commands through a web-browser has never been a good idea.  Does anyone remember ActiveX, or Microsoft Virtual Machine? (as in a proprietary Java engine and not in any way, shape or form, virtualization)  Quite frankly, its the laymen computer usage equivalent of handing an adolescent a loaded gun before knowing whether or not they know the first thing about gun safety.  At least if you're cutting and pasting, the code is the bullets, your command line is the gun and there is a very intentful action which has to take place in different graphical focuses in order to pull the trigger.

---

### Post by nilarimogard on 2010-03-17
It doesn't work for me. When I right click a command and select "Run selected command", a terminal opens with the following error: "There was an error creating the child process for this terminal" :(

---

### Post by Dayofswords on 2010-03-17
so far this is working for me, and i like it =)


here i'm to put a log of issues or problems i may see while using it(expect this to be edited)

[LIST]
[*]while having no command saved, right clicking without a highlight, selecting foxrunner, you are given a selctable but not clickable "Run command..." (see attachment 1), same with "run script...",EDIT: oh look its a tiny selectbox to the right <unconfirmed>
[/LIST]

---

### Post by lovinglinux on 2010-03-17
> **nilarimogard said:**
> It doesn't work for me. When I right click a command and select "Run selected command", a terminal opens with the following error: "There was an error creating the child process for this terminal" :(

I will investigate that. Thanks.

> **Dayofswords said:**
> so far this is working for me, and i like it =)

here i'm to put a log of issues or problems i may see while using it(expect this to be edited)

[LIST]
[*]while having no command saved, right clicking without a highlight, selecting foxrunner, you are given a selctable but not clickable "Run command..." (see attachment 1), same with "run script...",EDIT: oh look its a tiny selectbox to the right <unconfirmed>
[/LIST]

You are correct. I haven't thought about that. The menu shouldn't be displayed if there isn't any commands to show. That's the problem. The tiny empty selectbox is an empty menu list.

I'm currently implementing some new stuff, so I'm going to look at this soon.

---

### Post by Muppeteer on 2010-03-17
Although it's a good idea, i do not approve of laziness. Typing commands is the only way to learn, not copy/pasting either. C'mon, we're not windows users...

---

### Post by lovinglinux on 2010-03-17
> **Muppeteer said:**
> Although it's a good idea, i do not approve of laziness. Typing commands is the only way to learn, not copy/pasting either. C'mon, we're not windows users...

Seriously? So let's remove tab completion, command history and other useful stuff too.

---

### Post by kyfho23 on 2010-03-17
I'm getting the same error message as nilarimogard. But I'm leaving this installed, in hopes of an update fixing the problem. For what it's worth, I'm on an x64 system, using 3.6 .

---

### Post by gymophett on 2010-03-17
Wow, that's actually a very interesting idea.

Thanks!

---

### Post by JoeWheeler on 2010-03-17
Wow, that's great! Really good add-on:D

---

### Post by Najmudin on 2010-03-17
Great ,thank you for this extension.:KS

---

### Post by 2hot6ft2 on 2010-03-17
I installed it yesterday and forgot all about it until I saw this thread again. I just gave it a trial run with the ```
sudo apt-get update
``` and it worked great and no errors. Just have to remember it's there now for when I have a use for it.;)

---

### Post by lovinglinux on 2010-03-18
> **nilarimogard said:**
> It doesn't work for me. When I right click a command and select "Run selected command", a terminal opens with the following error: "There was an error creating the child process for this terminal" :(

> **kyfho23 said:**
> I'm getting the same error message as nilarimogard. But I'm leaving this installed, in hopes of an update fixing the problem. For what it's worth, I'm on an x64 system, using 3.6 .

I'm about to release a new version with lots of improvements, so could you please tell me what terminal do you use regularly and which one is setup in the extension preferences?

---

### Post by lovinglinux on 2010-03-18
I have just uploaded a new version with several of improvements.

Please test it and tell me what you think.

Changelog:

[LIST]
[*]new blacklist system to block dangerous commands
[*]new whitelist system to allow running commands only from trusted sites
[*]new options to exhibit a confirmation dialog when running commands locally or from web sites
[*]fixed problem with commands and variables added from the sidebar not showing in the context menu until a restart
[*]removed some options from the status bar icon for better integration
[*]added a warning that the user must agree before running commands
[/LIST]

---

### Post by nilarimogard on 2010-03-18
> **lovinglinux said:**
> I'm about to release a new version with lots of improvements, so could you please tell me what terminal do you use regularly and which one is setup in the extension preferences?

I'm using Gnome terminal and this is also set up in the preferences. I'm on Ubuntu Karmic 32bit, Firefox (actually Swiftfox) 3.6.

---

### Post by lovinglinux on 2010-03-18
> **nilarimogard said:**
> I'm using Gnome terminal and this is also set up in the preferences. I'm on Ubuntu Karmic 32bit, Firefox (actually Swiftfox) 3.6.

You get the error when trying to run a command or a script? Which command?

---

### Post by -grubby on 2010-03-18
Awesome work!

---

### Post by nilarimogard on 2010-03-18
> **lovinglinux said:**
> You get the error when trying to run a command or a script? Which command?

Any command!

---

### Post by forrestcupp on 2010-03-18
Awesome idea.  I wonder if it's possible to have keyboard shortcuts so you don't have to go through 2 pop-up menus.

---

### Post by lovinglinux on 2010-03-25
> **kernelhaxor said:**
> how about adding the 'Run in terminal' option to your extension? .. so I could get it all by just installing one add-on

In the new version, commands are executed in a terminal by default, but you can also choose to run it without a terminal, by using the options "Prompt for confirmation when running commands". The prompt itself has an option to change the default behavior.

When you save scripts now, you must select the option if they will run in a terminal or not. The will be executed automatically according to selected option.

> **DillByrne said:**
> maybe a feature to open certain profiles for your shell , or different shells

I'm considering this for future versions.

> **DoktorSeven said:**
> I'm wondering if a page could be constructed to automatically run a malicious command with that extension installed...

but that's just the paranoid, security-crazy GNU/Linux guy in me. :)

I have included in the latest version a permission functionality, that prevent running commands from unauthorized web sites. This is probably unnecessary, since the extension doesn't have any code that would allow a web site to start it's functions anyway. The extension works essentially by copying the command to the clipboard and parsing it to the terminal. Nevertheless, I'm providing this functionality as a "paranoid" mode and to avoid running commands accidentally. Additionally, I also included an option to request confirmation before running commands from sites and another option to request confirmation before running commands from the database. These confirmation dialogs also allow to choose if the command will be executed on a terminal or not. 

I also included a command blacklist functionality, that prevent commands containing certain keywords from running. You can add your own keywords to the list, but it comes already with some examples.

All these security layers can be disable/enabled in the extension preferences.

> **madjr said:**
> can you highlight a bunch of lines of text/commands and get them executed in 1 go ?

The new version allows to edit the command before running it, so you can add the necessary ampersands to multiple line codes. I will try to improve this on future releases, to add the ampersands automatically.

> **toupeiro said:**
> This could be very good, or *very* bad...  Historically speaking, running server-side code in userspace that invokes system commands through a web-browser has never been a good idea.  Does anyone remember ActiveX, or Microsoft Virtual Machine? (as in a proprietary Java engine and not in any way, shape or form, virtualization)  Quite frankly, its the laymen computer usage equivalent of handing an adolescent a loaded gun before knowing whether or not they know the first thing about gun safety.  At least if you're cutting and pasting, the code is the bullets, your command line is the gun and there is a very intentful action which has to take place in different graphical focuses in order to pull the trigger.

Is not server-side. The commands are executed by copying the text from the cached page and parsing the value to the extension function, which resides in a privileged chrome. So it is basically copy and paste. The user needs to actively select the text and click the menu to run the command. So there is not really an interaction between the web page scripts and the extension. 

Considering that the extension now offers a command blacklist, it is safer than letting the user copy any commands from any tutorial. Perhaps I could include more keywords to block in future releases. Any suggestions about dangerous commands would be much appreciated.

> **nilarimogard said:**
> It doesn't work for me. When I right click a command and select "Run selected command", a terminal opens with the following error: "There was an error creating the child process for this terminal" :(

> **nilarimogard said:**
> Any command!

I couldn't reproduce this problem yet. I have successfully executed commands using gnome-terminal, konsole and x-terminal-emulator. The later is the default option now.

The extension doesn't really run the command directly. It creates a temporary shell script and runs it. Have you tried to run scripts instead of commands? also try to run a command without terminal (there is an option now). Like for example:

```
firefox -P -no-remote
```

See if that works.

> **forrestcupp said:**
> Awesome idea.  I wonder if it's possible to have keyboard shortcuts so you don't have to go through 2 pop-up menus.

Yes, it is possible. I guess the best option would be to offer a customizable shortcut. I will look into it.

---

### Post by Doctor Mike on 2010-03-25
Cool, with this tool I could advance to become a super-advanced-intermediate-noob-ubuntu-geek.

---

### Post by malspa on 2010-03-25
Sounds like a good idea!  Looks like some people like it!

Am I "Tired of copying and pasting commands from forum posts?"

No.

That is not a criticism, just speaking for myself! Interesting stuff, though!  Another way of doing things, I guess.  Looks like a nice extension!  Great work!

---

### Post by lovinglinux on 2010-03-25
I have uploaded today **[COLOR="Sienna"]version 1.0.2[/COLOR]**. I strongly recommend upgrading, because this version fixes a few bugs. It also brings new features like command history and a much better interface. See new screenshots and new video demo.

Please test it and report any bugs.

---

### Post by lovinglinux on 2010-03-29
A new version of FoxRunner is available.

This version brings a built-in script editor, code improvements and a couple of new features.

---

### Post by Psumi on 2010-03-29
Too bad I use midori.

Also, what are its dependencies? I need to know if it'll run on Openbox, LXDE, XFCE, KDE or GNOME.

---

### Post by lovinglinux on 2010-03-29
> **Psumi said:**
> Too bad I use midori.

Also, what are its dependencies? I need to know if it'll run on Openbox, LXDE, XFCE, KDE or GNOME.

There are no dependencies. You can specify the terminal emulator on the extension preferences, according to your distro. I have tested it with gnome-terminal, konsole and x-terminal-emulator.

---

### Post by Psumi on 2010-03-29
> **lovinglinux said:**
> x-terminal-emulator.

Thank you, this is the one I needed, since x-terminal-emulator is updated when I remove or install a new terminal program (IE: LXTerminal.)

---

### Post by lovinglinux on 2010-03-29
> **Psumi said:**
> Thank you, this is the one I needed, since x-terminal-emulator is updated when I remove or install a new terminal program (IE: LXTerminal.)

Yup, that's why I put it as default. Here it points to gnome-terminal.

---

### Post by Jackelope on 2010-03-30
Great idea! Any chance of a Chromium port?

---

### Post by lovinglinux on 2010-03-30
> **Jackelope said:**
> Great idea! Any chance of a Chromium port?

Unfortunately not in the near future. I don't have the skills or the time to do it right now, but since the extension is released under GPL, anyone is free to do it. Besides, Chrome doesn't even work here.

---

### Post by lovinglinux on 2010-03-30
> **Dayofswords said:**
> so far this is working for me, and i like it =)


here i'm to put a log of issues or problems i may see while using it(expect this to be edited)

[LIST]
[*]while having no command saved, right clicking without a highlight, selecting foxrunner, you are given a selctable but not clickable "Run command..." (see attachment 1), same with "run script...",EDIT: oh look its a tiny selectbox to the right <unconfirmed>
[/LIST]

Fixed in the version I have just uploaded (1.0.4).

---

### Post by Toost Inc. on 2010-04-14
> **nilarimogard said:**
> It doesn't work for me. When I right click a command and select "Run selected command", a terminal opens with the following error: "There was an error creating the child process for this terminal" :(

I´m having the same problem and was actually going here hoping there was a solution :P.
However I did find that when the error occurs, and you keep the empty Terminal window open, that when you try again. it now WILL work, opening in a new window.

I tried this both with x-terminal-emulator and gnome-terminal with the same results. I also tried installing terminator, but with terminator you just see a new window flicker by and close again. As does x-terminal-emulator with terminator installed. 

I´m using karmic 32bit and Firefox 3.6.3

Anyway, I hope this helps and thanks for the still very useful extension

---

### Post by lovinglinux on 2010-04-14
> **Toost Inc. said:**
> I´m having the same problem and was actually going here hoping there was a solution :P.
However I did find that when the error occurs, and you keep the empty Terminal window open, that when you try again. it now WILL work, opening in a new window.

I tried this both with x-terminal-emulator and gnome-terminal with the same results. I also tried installing terminator, but with terminator you just see a new window flicker by and close again. As does x-terminal-emulator with terminator installed. 

I´m using karmic 32bit and Firefox 3.6.3

Anyway, I hope this helps and thanks for the still very useful extension

Thanks for the info. That is really weird.

---

### Post by Ric_NYC on 2010-04-14
Parabens!


Congratulations!

---

### Post by lovinglinux on 2010-04-14
I just released version 1.0.5, which has been approved by Mozilla, so now you can get updates automatically, through Firefox add-on manager. Please install the new version to make sure you will get future updates.

Additionally, I received some encouraging comments from the editor who reviewed and approved FoxRunner. He said:

> **I liked very much how seriously you took the security of your add-on users. Keep up the good work!**

*[Jorge Villalobos](https://forums.addons.mozilla.org/memberlist.php?mode=viewprofile&u=4230) -- Mozilla’s Add-on Developer Relations Lead*

I really appreciated such feedback, specially considering the nature of FoxRunner. I’m sure this will give some peace of mind to users worried about the extension security. I have included some notes about the security model of FoxRunner on the first post.

Unfortunately I couldn't find yet what is causing the problem on some users systems, that prevents any command from running. Still working on that tho. I will post an update as soon as I can find the culprit.

---

### Post by Dayofswords on 2010-04-18
when running a command, when it finishes, is it suppose to exit the terminal


if yes, is it possible to have an option to keep it open after it completes?
(i'm thinking of a command i just ran "lspci | grep VGA", to find info on my video card, it exit before i could read the output)
but so far so good

---

### Post by lovinglinux on 2010-04-18
> **Dayofswords said:**
> when running a command, when it finishes, is it suppose to exit the terminal


if yes, is it possible to have an option to keep it open after it completes?
(i'm thinking of a command i just ran "lspci | grep VGA", to find info on my video card, it exit before i could read the output)
but so far so good

This has also been a request from Mozilla editor for the next version. So, I will implement soon. Meanwhile, you can change the way the terminal behaves in emulator preferences.

Thanks for the feedback.

---

### Post by Toost Inc. on 2010-04-30
As a suprprising bonus, upgrading to Lucid Lynx apparently fixed the problem of not being able to open a child process!

especially sudo commands seem to be working perfectly now. I got two more errors when testing ls and echo but those commands ran fine after that as well...

So...yeah, apparently I´m fixed now, uhm, thanks!

---

### Post by lovinglinux on 2010-04-30
> **Toost Inc. said:**
> As a suprprising bonus, upgrading to Lucid Lynx apparently fixed the problem of not being able to open a child process!

especially sudo commands seem to be working perfectly now. I got two more errors when testing ls and echo but those commands ran fine after that as well...

So...yeah, apparently I´m fixed now, uhm, thanks!

Great. Ironically, I started experiencing this problem with Lucid. It doesn't occur all the time, just occasionally. I'm currently in the process of beta testing a new version of another extension, but I will look into this soon.

Please give some feedback about the usability when you can.

---

### Post by Toost Inc. on 2010-04-30
Yeah, about that, I thought I might have been a bit hasty so I restarted Firefox and tried again...Seems I WAS a bit hasty, now I´m back at square one.

But yeah, It was a good run while it lasted. No idea what caused it to work the first time though

---

### Post by lovinglinux on 2010-04-30
> **Toost Inc. said:**
> Yeah, about that, I thought I might have been a bit hasty so I restarted Firefox and tried again...Seems I WAS a bit hasty, now I´m back at square one.

But yeah, It was a good run while it lasted. No idea what caused it to work the first time though

Try to run a command, if it gives you the child process issue, try again the same command to see if it works. It is not a solution, but will help me troubleshoot.

---

### Post by lovinglinux on 2010-04-30
I will setup a beta channel for this extension, in order to allow users experiencing problems with the stable release to test the latest code. I'm also going to work on this issue today. So expect the release of the first pre-release version today or tomorrow.

---

### Post by lovinglinux on 2010-07-26
Soon I will release the new version of FoxRunner, which brings several improvements in the underlying code and a few new features, like an option to keep the terminal open after executing commands and a new command toolbar.

Here is a short demo of the new command toolbar, which replaces the old icon launcher and allows to type and run commands from Firefox status bar, without requiring to click any additional dialog, unless of course if you set FoxRunner to prompt for confirmations, as demonstrated in the video.

[http://foxrunner-extension.blogspot.com/2010/07/foxrunner-106-on-its-way.html](http://foxrunner-extension.blogspot.com/2010/07/foxrunner-106-on-its-way.html)

If you have any suggestions or complains to be considered for the next version, this is the time to speak up.

---

### Post by lovinglinux on 2010-08-01
FoxRunner 1.0.6 is now available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixes the child process error and also brings some new features, like real-time search in the sidebar, support for wildcards in the blocked command list and a new status bar command runner.

This version is already compatible with the latest Firefox 4 Beta.

---

### Post by lovinglinux on 2010-08-01
I'm creating a new thread for the new version and will ask a moderator to close this one.

Please visit [http://ubuntuforums.org/showthread.php?t=1543783](http://ubuntuforums.org/showthread.php?t=1543783)

---

### Post by cariboo on 2010-08-01
Closed by request.

---

