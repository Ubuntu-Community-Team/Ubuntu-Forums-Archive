---
title: "Gnome Shell: how to reach applications list without using a mouse"
date: 2012-01-03
forum: The Cafe
---

### Post by keithpeter on 2012-01-03
Hello All

I've finished the month or so using Unity2d as my main interface. Now I'm trying Gnome Shell as installed on 12.04 from the Ubuntu repository. This is part of a personal project to understand the design ideas behind the 'new' interfaces.

To see a list of applications, I currently

[LIST=1]
[*]Tap Windows/Super/Mod4 key to bring up the Activities overlay thingy
[*]By default, the overlay thingy always has Windows selected
[*]I click on Applications with the mouse
[/LIST]

Is there a way of completing the last step using only the keyboard? See the screen grab for what I'm on about.

I've checked

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

Cheers

---

### Post by BigSilly on 2012-01-03
Your best bet, if I'm understanding you properly, would be to add the applications menu button from [here]("https://extensions.gnome.org/extension/6/applications-menu/"). That way you wouldn't have to use the shell overlay.

---

### Post by keithpeter on 2012-01-03
Hello BigSilly and all

Yes, but that would be cheating :twisted:

My little game here is to work with the default settings of each of the 'new' interfaces (Unity2d, Gnome Shell) for a month or so.

I might make another user account and add a few extensions to see what effect they have on typical tasks. 

Another part of my little game is to imagine (complete fantasy, snowball in hades) we had GNU/Linux on all the student and staff computers at the College where I work (a thousand screens or so). *No way* will IT techs be customising an install. Default is what you get!

I've worked out that there *isn't any form of keyboard navigation* around the overlay thingy, but that you can just type the name of an application (if you know the name) and it will appear. Oddly, you *can* type part of the name and then use the arrow keys to navigate the dynamic results list. Strangely inconsistent.

Cheers

---

### Post by Seq on 2012-01-03
> **keithpeter said:**
> Yes, but that would be cheating :twisted:

My little game here is to work with the default settings of each of the 'new' interfaces (Unity2d, Gnome Shell) for a month or so.

I might make another user account and add a few extensions to see what effect they have on typical tasks.

Part of the points for gnome-shell is that it is extensible. Ignoring that is like buying a sports car and doing the speed limit.

There are a few extensions that would aid keyboard navigation: [Window Navigator]("https://extensions.gnome.org/extension/10/windownavigator/") allows selection of windows in the overlay via alt+N keystroke, [gtile]("https://extensions.gnome.org/extension/28/gtile/") makes working with multiple windows great. There are plenty of additional extensions that are easily addable via [extensions.gnome.org/]("https://extensions.gnome.org/") (though only in firefox currently -- GNOME 3.4 will support chrome).

As for your situation -- those navigating by keyboard alone are likely to know the name of what they want to run. Those who want to hunt and peck are more likely to use the mouse (or only hunt-and-peck once anyway).

> **keithpeter said:**
> Another part of my little game is to imagine (complete fantasy, snowball in hades) we had GNU/Linux on all the student and staff computers at the College where I work (a thousand screens or so). *No way* will IT techs be customising an install. Default is what you get!

I'd hope they would customize it. Does your school not have shared directories? No remote homes? No special addressing or printer configuration? Installing an extension by default is not a lot of work.

---

### Post by keithpeter on 2012-01-03
> **Seq said:**
> Part of the points for gnome-shell is that it is extensible. Ignoring that is like buying a sports car and doing the speed limit.

Hello Seq

Thanks very much for these suggested extensions, and I'm assuming that extensions are on a per user basis and so I shall set up a second 'extended shell' user and try them.

I don't know about sports cars, but I do know how IT gets managed in small to medium sized organisations and its ugly :twisted:

---

### Post by yugnip on 2012-01-03
When you hit the windows key and see the Dash Window view, just begin typing which app, file, mp3, movie, etc that you want, and choose it in the list. You can use arrow keys to jump/scroll through the choices.

I use a laptop as my main machine, and Shell is super handy for keeping my butterfingers away from the trackpad.

---

### Post by Copper Bezel on 2012-01-03
Yeah, the "Applications" view is inherently mouse-driven, so there's no point in having a keystroke to switch to it, because you couldn't get to the app from there without a lot of tabbing around with arrow keys. The assumption is that if you're using the Overview from the keyboard, you type the name of whatever you're looking for.

Window switching from the Overview is exclusively mouse-driven, though, unless you use an extension like the Windows Navigator. (There's a better one that uses the arrow keys instead of the numerals, but I don't remember the name. I use an extension that assigns the arrow keys to workspace switching in the Overview instead.)

---

### Post by Seq on 2012-01-03
> **keithpeter said:**
> Hello Seq

Thanks very much for these suggested extensions, and I'm assuming that extensions are on a per user basis and so I shall set up a second 'extended shell' user and try them.

If you install them as a user, then yes they are per-user.

They could be installed system-wide (via package, or other means) and apply to all users. The extensions.gnome.org website won't (can't, actually) do that.

> **keithpeter said:**
> I don't know about sports cars, but I do know how IT gets managed in small to medium sized organisations and its ugly :twisted:

I've been in a few. I guess I'm just lucky enough to usually be the guy doing it.

---

### Post by cbowman57 on 2012-01-03
No way that I know of, I'd like to at least have the option of using the tab key to advance to the next displayed app.

This is a missing feature IMO.

---

### Post by keithpeter on 2012-01-03
Hello all

@Seq

> **Seq said:**
> I've been in a few. I guess I'm just lucky enough to usually be the guy doing it.

OK, at work I can log on to any PC in the organisation and get my desktop with my files. This is MS Windows, and I understand its active directory stuff with policies. The programs are on each PCs hard drive because I've noticed slight version differences from room to room.

How does that get done with linux servers and clients? Do the home drives come off a server? Or just the dotfiles?

> **Copper Bezel said:**
> Window switching from the Overview is exclusively mouse-driven, though, unless you use an extension like the Windows Navigator. (There's a better one that uses the arrow keys instead of the numerals, but I don't remember the name. I use an extension that assigns the arrow keys to workspace switching in the Overview instead.)

@Copper Bezel: Thanks, I've learned already that Gnome Shell is very extendable and can be customised easily, even through the Web browser. This will cause issues for training materials though! I can see administrators blocking the extension web sites as well for the sake of clarity. I can also see 'playful' users installing extensions that conflict.

@yugnip: yes thanks I found out about the 'just type' bit, and yes I normally use dmenu on the netbook for the same reason.

Quite a change all this isn't it?

---

### Post by Seq on 2012-01-03
> **keithpeter said:**
> OK, at work I can log on to any PC in the organisation and get my desktop with my files. This is MS Windows, and I understand its active directory stuff with policies. The programs are on each PCs hard drive because I've noticed slight version differences from room to room.

How does that get done with linux servers and clients? Do the home drives come off a server? Or just the dotfiles?

Starting fresh and just Linux? I'd mount /home over nfs, and do authentication through LDAP (there is more to just doing that, though).

However, if you already have an AD, it might be worthwhile to look at 'likewise-open'. It's available in Ubuntu's repositories, and works more or less like you're familiar: "Joins" your Linux machine to an AD domain, converts AD users and groups to be usable in Linux, etc. It will allow you to have any user log on to the machine, and automatically create /home/$USER on first run. I've used it previously, the only issue I had was having to log in as "DOMAIN\USER", though that may be configurable.

You'd probably still want /home mounted over nfs to share them (as opposed to cifs. probably won't work right, but I've never actually tried), and if you want the auto-create thing to work, the /home mount will probably need no_root_squash specified on the export.

Now, if you get the same desktop on every windows machine, it sounds like you've got AD roaming profiles. Not sure how or if likewise handles that.

---

### Post by keithpeter on 2012-01-03
> **Seq said:**
> Now, if you get the same desktop on every windows machine, it sounds like you've got AD roaming profiles. Not sure how or if likewise handles that.

Hello Seq

Thanks for a full answer there, enough to focus some reading. Yes we have roaming profiles, its all MS at work with a few MacOS rooms.

Cheers

---

### Post by Werekitten on 2012-01-04
> **keithpeter said:**
> Hello All

I've finished the month or so using Unity2d as my main interface. Now I'm trying Gnome Shell as installed on 12.04 from the Ubuntu repository. This is part of a personal project to understand the design ideas behind the 'new' interfaces.

To see a list of applications, I currently

[LIST=1]
[*]Tap Windows/Super/Mod4 key to bring up the Activities overlay thingy
[*]By default, the overlay thingy always has Windows selected
[*]I click on Applications with the mouse
[/LIST]

Is there a way of completing the last step using only the keyboard? See the screen grab for what I'm on about.

I've checked

[https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

Cheers

Of course. There's a (customizable) keyboard shortcut to navigate between Shell UI elements. 
I have it set to Ctrl+Tab, but your setting may be different. 
Youll' find it in System Settings > "Keyboard" capplet > "Shortcuts" tab > "Navigation" list item > "Switch system controls" entry.

Let me add, anyway, that if you are interested in the ideas and the design that follows, that you're supposed to rarely need to navigate to the whole grid of available applications. Hit Meta key, then start typing and the applications will be searched based on what you type. Basically by design that grid view of all applications is for apps that you rarely use (they are not in your dash) and are not sure about when it comes to description or name (that would be covered by the search-as-you-type).

---

### Post by keithpeter on 2012-01-04
> **Werekitten said:**
> Basically by design that grid view of all applications is for apps that you rarely use (they are not in your dash) and are not sure about when it comes to description or name (that would be covered by the search-as-you-type).

Thanks Werekitten

Useful to know about that setting that is presumably part of core Gnome Shell and not a user extension.

'By design' is one thing, what real people actually will do is another :twisted:

---

