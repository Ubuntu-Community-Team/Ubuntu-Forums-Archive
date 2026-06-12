---
title: "Setting Compiz options in PP - what's the plan?"
date: 2012-01-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-11
I've asked it during OO cycle, no one knew for sure. I still have the same question,  now for PP. AFAIK, ccsm won't ship by default. If a user decides to change something...

- Basic, that doesn't even relate to effects: Change number of desktops, use a color filter for Myopia, etc. 
- That Relates to effects, but still very primary: Enable/disable/change something like alt+tab behavior, tweak something to avoid artifacts, maybe change something pretty basic in Unity (like the Launcher behavior), etc.

Despite hacking it manually, which I feel like it's undoable for the common individual, or using third-party apps (like Ubuntu Tweak), what are the options? Are (at least) some of compiz/unity settings gonna migrate to gnome-control-center? I still can't find any lead on what the plan for that is. Anyone know anything about it?

Thanks,
Effenberg

---

### Post by lucazade on 2012-01-11
+1

I believe the answer is in this [post]("http://design.canonical.com/2012/01/system-settings-for-precise/") and especially in this document:
[Gnome 3 System Settings changes]("https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB")

I want to hope they will integrate unity options inside the stock system settings applet of Gnome3.

---

### Post by scradock on 2012-01-11
> **lucazade said:**
> +1

I believe the answer is in this [post]("http://design.canonical.com/2012/01/system-settings-for-precise/") and especially in this document:
[Gnome 3 System Settings changes]("https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB")

I want to hope they will integrate unity options inside the stock system settings applet of Gnome3.
Well, I read through the document - no sign of ANY acknowledgement of the "Basic" compiz options the effenberg quoted, let alone the "cube" and "cube rotate" that we all loved so much a few years back. It's looking as if all the awesome compiz effects have been abandoned, and it has been determined that users shall have no way to get them back or customize them, while the entire overhead built up to support them is still there because Unity needs them - even on a system set to use Gnome Shell!

What a mess!!!!

---

### Post by grahammechanical on 2012-01-11
As someone for whom the comment > undoable for the common individual applies (well, almost applies and I am not offended), I would like to see Unity settings as a utility in System Settings. I would like it to include working Compiz effects with the non-working effects left out until they are proven to work.

But, Compiz is not controlled by Canonical. The Compiz developers will continue to develop it. And so long as a distribution includes a terminal it will always be possible for people to break their systems and then demand that someone on this forum fix it.

Such is life.

I bet, that if ever we get Ubuntu embedded in handheld devices it will have a very limited capability to be modified.

Regards.

---

### Post by ventrical on 2012-01-11
> **lucazade said:**
> +1

I believe the answer is in this [post]("http://design.canonical.com/2012/01/system-settings-for-precise/") and especially in this document:
[Gnome 3 System Settings changes]("https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB")

I want to hope they will integrate unity options inside the stock system settings applet of Gnome3.


  I didn't see anything about compiz... mabey thats the point ? :)

---

### Post by ventrical on 2012-01-11
> **grahammechanical said:**
> As someone for whom the comment  applies (well, almost applies and I am not offended), I would like to see Unity settings as a utility in System Settings. I would like it to include working Compiz effects with the non-working effects left out until they are proven to work.

But, Compiz is not controlled by Canonical. The Compiz developers will continue to develop it. And so long as a distribution includes a terminal it will always be possible for people to break their systems and then demand that someone on this forum fix it.

Such is life.

I bet, that if ever we get Ubuntu embedded in handheld devices it will have a very limited capability to be modified.

Regards.

Compiz*is* supported by Canonical , just not ccsm. No compiz, no Unity.

Basically .. without compiz Ubuntu just becomes another flatspace.

---

### Post by effenberg0x0 on 2012-01-11
Please keep in mind I have never stopped to look at ccsm / gnome-control-center code. A couple questions:

- Wild guessing: Doesn't it just read / write to /schemas/apps/compiz-1/plugins/<some_plugin><some_property>? I mean, we're all used to eventuallysetting stuff manually via gconftool-2.
```
 
gconftool-2 --dump / | grep -i compiz-1

```

- Inserting something into gnome-control-center: Isn't it just a loadable C/C++/Python/Whatever + GTK, probably with a reasonably well detailed API somewhere? 

Unless I'm really tripping here, it doesn't sound complex at all to put compiz plugins config inside gnome-control-center. So, it makes me think that, if it hast been done yet, it probably is not in the plans to do it. A programmer that is familiar with the code for these two (ccsm / gnome-control-center) could do it in a day of work.

---

### Post by grahammechanical on 2012-01-11
And yet there is a Unity plugin in CCSM. How did that get there? And CCSM is not installed by default and you find it in the Dash, not in System Settings. To me it seems like an after thought or a stop gap. The Unity settings are described as experimental.

Still, Ubuntu and indeed all of Linux is a project under development. I try to keep that in mind.

Regards.

---

### Post by effenberg0x0 on 2012-01-11
I had a (very) quick look at it. My opinion is that if they wanted an icon inside system settings (gnome-control-center) to control compiz plugins options (including unityshell), they could have done it easily. Doing something that works would take a day of work for an experienced programmer that is familiar with that code. Doing something Ayatana-ish would obviously take more, with all the design-politics involved. But it's doable.

I *think* they are aware that it's an illusion to believe that some users will not download ccsm (or a  3rd party tool) and play with compiz  anyway. And that taking away the average  users right to configure how many desktops / viewports he uses (which was  default in previous releases and most Linux desktops, composite or not) is not cool. 

At first I was thinking that one potential reason to justify why no access to compiz plugins settings was coded into the standard settings interface would be that these settings controls would have to also work somehow for Ubuntu-2D. And making config/features operate similarly in both desktops is a challenge. 

But then it struck me that they are probably prioritising making compiz more stable before allowing people to mess with it. And that would justify why smspillaz is under so much pressure - maybe his delay into making compiz more stable is what's holding back further development of Ubuntu UI/features/customisation. 

(OBS: Just a theory, as there's no official info anywhere)

---

### Post by ventrical on 2012-01-11
The guy is a self admitted failure , He posted that on Christmas day.

[http://smspillaz.wordpress.com/](http://smspillaz.wordpress.com/)

 We should try to help the guy out.

EDIT:

belay this msg . It has already been adressed in another forum.

---

### Post by kansasnoob on 2012-01-11
When I use Unity I use Unity-2D because I've always preferred Metacity, but recently on Ayatana I read that MyUnity may be included in Precise. Does MyUnity help with Compiz settings?

[https://launchpad.net/~myunity](https://launchpad.net/~myunity)

---

### Post by cariboo on 2012-01-11
The reason ccsm isn't included by default, is that it is felt that new users can and will make their system unusable by applying the wrong settings. Myunity is a simplified user interface to compiz, and makes it much harder to screw things up

---

### Post by ventrical on 2012-01-11
> **cariboo907 said:**
> The reason ccsm isn't included by default, is that it is felt that new users can and will make their system unusable by applying the wrong settings. Myunity is a simplified user interface to compiz, and makes it much harder to screw things up


That is really a nice piece of work but I cannot help but ask , why can't ccsm be shipped with a default config with a message , somewhat like CairoDock uses on first-run? Cairo Dock detects right off  if Open GL is functional-happy and then renders a message...

 so .. perhaps if <ccsm> were to do the same? I mean it had been suggested  by effenberg (and myself and others) that a message could be inserted during the install- ie;

 CompizConfig Setting Manager has detected Open GL.
 A default Compiz Setting file will be used that will Inlcude
Unity 3D. Other modifications to Settings  may cause instability.

---

### Post by cariboo on 2012-01-11
Most users don't pay attention to warnings, they are so busy looking for a way to cancel/close the message box, that they never read the content. I see this all the time, especially with average users.

---

### Post by ventrical on 2012-01-11
> **cariboo907 said:**
> Most users don't pay attention to warnings, they are so busy looking for a way to cancel/close the message box, that they never read the content. I see this all the time, especially with average users.

Yes... you are right.  They want that CD/USB freebie to work out of the box. No muss, no fuss - just give me the cube!! :)

   But perhaps if it were something more comprehensive.. sort of like -

'Ok .. you got Cube! If you play with the settings , you don't got Cube ! '

:)

jk

---

### Post by effenberg0x0 on 2012-01-11
> **cariboo907 said:**
> The reason ccsm isn't included by default, is that it is felt that new users can and will make their system unusable by applying the wrong settings. Myunity is a simplified user interface to compiz, and makes it much harder to screw things up

I understand. I personally prefer when applications have "basic" and "advanced" settings. "Basic settings" display 3 controls. If you select "Advanced settings", other controls show up, but a dialog tells you you're on your own. Maybe VNC is a good example of this.

But will this application ship with PP by default? This will be default interface a Linux user migrating from something else to Ubuntu will go to change the number of desktops, for example?

> **cariboo907 said:**
> Most users don't pay attention to warnings,  they are so busy looking for a way to cancel/close the message box, that  they never read the content. I see this all the time, especially with  average users.

So true. Average users click faster than they think. Sometimes they immediately regret clicks, 1 second after clicking, and start repeatedly pressing "esc" in hopes of cancelling stuff. More advanced users think faster than they click, think ahead of the interface/presented options.

**EDIT: **There was a discussion here a while ago, about if Ubuntu was getting "dumber" to become more adequate to normal people. I think the thread was poisoned by people who took that chance to bash Unity and ended in flmes as usual. But, in fact, as the OS UI designers choose to eliminate any interface that allows for advanced settings, it starts to feel weird to me - not Linux-like. I wish they would go for a more conservative 2-modes "basic/advanced" settings design, like the one I mentioned above (VNC example), as a way to please both newbies and experienced users.

---

### Post by cariboo on 2012-01-11
It looks like the designers are looking at including an applet in System Settings to customize Unity, but they don't mention what the application will be. See this blog post:

[http://design.canonical.com/2012/01/system-settings-for-precise/](http://design.canonical.com/2012/01/system-settings-for-precise/)

---

### Post by ventrical on 2012-01-12
> **cariboo907 said:**
> It looks like the designers are looking at including an applet in System Settings to customize Unity, but they don't mention what the application will be. See this blog post:

[http://design.canonical.com/2012/01/system-settings-for-precise/](http://design.canonical.com/2012/01/system-settings-for-precise/)


Why not just re-introduce simple CCSM? or better yet .. why did they  dump that little app from the repos in the first place?


[http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/)

---

### Post by jbicha on 2012-01-12
> **effenberg0x0 said:**
> I've asked it during OO cycle, no one knew for sure. I still have the same question,  now for PP. AFAIK, ccsm won't ship by default. If a user decides to change something...

- Basic, that doesn't even relate to effects: Change number of desktops, use a color filter for Myopia, etc. 


Color filter for myopia? My wife is very near-sighted and has never wanted to change the color filter. System Settings>Universal Access allows setting High or Low contrast easily.

Technically, System Settings was not designed to be extendable at all as the GNOME developers think that all approved core stuff should be there. Ubuntu ships a hacked System Settings which allows this to be more flexible. To do it right, you'd need to write your panel in C and yes, an average GNOME developer should be able to get something going in not too many hours. Ubuntu hasn't done this so far not necessarily because of "design politics" but because it's not completely clear how much of this extreme customizability should be exposed in the default install. Obviously, it's all still there in CCSM for the extreme tweakers.

And like you suggested, only a few options (number of workspaces, favorite apps) are shared between Unity and Unity 2D. The "cube" of course isn't possible in Unity 2D.

vetrical, "self admitted failure" sounds awfully harsh to the guy who's poured a lot of time and hard work into Compiz and Unity.

myunity is in Precise in the sense that is in the repositories; it will not be included in the default install.

---

### Post by ventrical on 2012-01-12
> **jbicha said:**
> 

vetrical, "self admitted failure" sounds awfully harsh to the guy who's poured a lot of time and hard work into Compiz and Unity.

myunity is in Precise in the sense that is in the repositories; it will not be included in the default install.


 It's not meant to  sound that way. Some posters are saying there is nothing 'official' and so the 'keeper' himself also seems to be struggling at how to build a workaround for  the ccsm problem. I just wanted to point that out , but , that also has been posted in a duplicate echo and hence I belayed that post.

  So here we are again, hacking at the same problem that we had with OO. I mean there are probably thousands of multifaceted opinions from every hacker on the planet about this problem and  mine is only one of them :)

  One of the ways I look at it is that Ubuntu/Unity/CCSM is a discovery process. When I took up the task to convert over to Linux Immersion I did all my own work, all my own asking and all my own searching.   The best way to  get resolution to these problems is to stand on the shoulders of giants, which I did, and humbly so - and , overall, it has made me a better Ubuntu operator. In some ways I could almost say that the Ubuntu Forums sort of held my hand at times and walked me through a lot of problems. Then, it is only fair for me to do the good deed in return for others, for newbies and veterans alike.  Thats is part of why the community is here in the first place, is it not ?

   Eventually there will be a mulitfaceted solution to this problem. In Ubuntu's short history there hasn't seemed to much to stand in the way of it's progress. In the meantime , we can lead a horse to water but  we can't make him drink it! :)

 As I posted in another echo .. for blacklisted video cards. etc.. I just download lubuntu-desktop  or xubuntu-desktop from the repos - until they unblock  whatever it is that they have to unhook with this Unity problem. I did not write Unity 3D. I'm just beta testing it. From what I see happening (from my experience) is that the Unity Plugin is just grabbing a lot of vanilla files and placing them on the desktop and hooking them to sub-directories. It is not a complex machine (program) as I see it. It appears to me that there are two core areas. The compiz-core and the Unity Desktop. The Unity desktop works fine by default without CCSM being installed but as soon as that is installed then the UnityPlugin seems to act as a traffic-cop to some of the other CCSM settings. That will happen also when you switch to GNOME classic. It seems that the compiz-core or the Unity-core programs won't unhook from each other. It won't 'mode-switch' so to speak. It's most likely  just a few lines of code but there seems to be a bigger problem and I think that sort of may be ubuntu-politics because if those few lines of code were changed then a lot of other depends would have to be re-written.

 However, as long as we keep hacking away at it .. it can only get better :)

---

### Post by effenberg0x0 on 2012-01-12
> **jbicha said:**
> Color filter for myopia? My wife is very near-sighted and has never wanted to change the color filter. System Settings>Universal Access allows setting High or Low contrast easily.

Lol, sorry, I mean daltonism, not myopia... I always wondered what those filters were for until I met a person that actually had to use them (deuteranopia, protanopia, swap-green-blue, etc) to be able to see anything. I'm not a doctor, and I know nothing about it, but it seems like some people depend on such features. There's info on this types of Daltonism in Wiki, but I hadn't had the time to read it.

> **jbicha said:**
> Technically, System Settings was not designed to be extendable at all as the GNOME developers think that all approved core stuff should be there. Ubuntu ships a hacked System Settings which allows this to be more flexible. To do it right, you'd need to write your panel in C and yes, an average GNOME developer should be able to get something going in not too many hours. Ubuntu hasn't done this so far not necessarily because of "design politics" but because it's not completely clear how much of this extreme customizability should be exposed in the default install. Obviously, it's all still there in CCSM for the extreme tweakers.

That's how Ubuntu One icon got in there, for example? I was hoping to find some free time tomorrow to study gnome-control-center and was thinking I should look at Ubuntu One as an example.
> **jbicha said:**
> 
And like you suggested, only a few options (number of workspaces, favorite apps) are shared between Unity and Unity 2D. The "cube" of course isn't possible in Unity 2D.
myunity is in Precise in the sense that is in the repositories; it will not be included in the default install.

Thanks for the tips JBicha :)

---

### Post by effenberg0x0 on 2012-01-12
@JBicha Just one more question. When you mention:
> **jbicha said:**
> ... Ubuntu hasn't done this so far not necessarily  because of "design politics" but because it's not completely clear how  much of this extreme customizability should be exposed in the default  install...

Ubuntu has been my choice of distro, for fun an profit, for a while and I got nothing against it's evolution from the standard "any distro" UI to Unity and it's modernisation. But I do feel like having no GUI for some advanced settings, while safer for the average user, is a little weird for those that are used to a Linux desktop for a while. In your opinion, is there room for a proposition to adopt Basic/Advanced settings switches (like the VLC example I mentioned earlier, but see the two screenshots) in the future? Or is there a solid consensus among Ubuntu developers to adopt this UI simplification as the default/only settings mode?

Example: VLC Basic Settings
[ATTACH]210682[/ATTACH] 

Example: VLC Advanced Settings
[ATTACH]210683[/ATTACH]

---

### Post by jbicha on 2012-01-13
> **effenberg0x0 said:**
> Lol, sorry, I mean daltonism, not myopia... I always wondered what those filters were for until I met a person that actually had to use them (deuteranopia, protanopia, swap-green-blue, etc) to be able to see anything. I'm not a doctor, and I know nothing about it, but it seems like some people depend on such features. There's info on this types of Daltonism in Wiki, but I hadn't had the time to read it.

That's how Ubuntu One icon got in there, for example? I was hoping to find some free time tomorrow to study gnome-control-center and was thinking I should look at Ubuntu One as an example.

I don't know much about color blindness, but I do know that bugs are regularly accepted and fixed to make things better for those people. One recent example is [gnome-system-monitor]("https://launchpad.net/ubuntu/+source/gnome-system-monitor/3.3.3-0ubuntu1"). You should look into the [Ubuntu Accessibility Team]("https://wiki.ubuntu.com/Accessibility") if you'd like to work on improving stuff like that.

A goal for Precise is to remove the external (pop-up) windows that were hacked into System Settings for Precise and replace them with built-in panels so a better example to look at would be Backup (Deja Dup) or indicator-datetime.

Personally, I think the Ubuntu design is relatively simple by default (but including the stuff most people want), but additional system settings can be available for additional install. So something like gnome-tweak-tool or the Unity tweaks are cool. If a plugin could be installed to add extra settings that would be awesome too. I can't speak for the Design Team though.

---

### Post by hawthornso23 on 2012-01-15
I no longer `trust' that compiz will ever come back. Compiz seems to have been cannibalized to build unity and the people who destroyed it  have absolutely no interest in ever putting it back in working condition. They are happy to see it gone. That is why they killed it. They wanted it dead.

Who are these people? They are the hair shirt usability people who seem to have taken over Gnome and also Ubuntu recently. These people take themselves and their work seriously, and they expect the rest of us to take it seriously too. Frivolity is definitely out. And customizability simply cannot be tolerated because desktop design is a job for serious experts who know what is best for everyone ... in the opinion of these serious experts.

Compiz is everything that the hair shirt brigade hates. Compiz is all  about doing amazingly cool and totally frivolous stuff with your desktop  environment simply because ... you can! Compiz is about configurable  everything. These people hate cool and frivolous stuff. They are serious  people and they think user interfacer design is serious work. We can't  have anybody having FUN with it! Users are not supposed to ENJOY using  ubuntu. We are all supposed to admire how efficient the design is. They  can't stand the thought of people actually configuring their own  desktops..


Ubuntu has lost its soul. It used to be about cool. It used to be about fun. But these days we are  supposed to be using ubuntu ... efficiently ... and admiring what a clever and efficient user interface that the experts have designed. These days Ubuntu wants to be "serious and well designed and efficient and standardized and corporate" ... and as boring as hell.

---

### Post by jbicha on 2012-01-15
Hair shirt people?

And if you're not having fun with Ubuntu, I think you're doing it wrong. Ubuntu's still just as fun here as it's always been! :-)

---

### Post by kyleabaker on 2012-01-15
> **jbicha said:**
> Hair shirt people?

And if you're not having fun with Ubuntu, I think you're doing it wrong. Ubuntu's still just as fun here as it's always been! :-)

I agree. Plus, ranting isn't beneficial to anyone here and is frankly a bit off topic. At least add some constructive criticism.

---

### Post by effenberg0x0 on 2012-01-15
Sorry for the OT, I have searched quite a bit couldn't find a proper definition for "hair shirt" I think. Is this definition correct?
From: [http://idioms.thefreedictionary.com/a+hair+shirt](http://idioms.thefreedictionary.com/a+hair+shirt)
> if someone wears a hair shirt, they choose to make their life unpleasant  by not having or experiencing anything that gives them pleasure.
"I don't think you have to put on a hair shirt in order to be a socialist."Just asking out of curiosity. I cant understand how the definition fits with the rest.

**EDIT: **After thinking about it for a while, I realise that if Compiz / Unity developers are stuck with shirts made of hair, which are probably incredibly ugly and itchy, we should join efforts to provide them with a better / more comfortable / socially acceptable wardrobe. That could effectively lead to faster and better coding. I mean, Sam is already tired and stressed, we all know it. Give the man a decent / not-disgusting shirt made of a normal fabric for God sake. I bet many of them are choosing to code shirtless, through the cold whether, than to wear such abominations.

---

### Post by lucazade on 2012-01-26
> **lucazade said:**
> +1

I believe the answer is in this [post]("http://design.canonical.com/2012/01/system-settings-for-precise/") and especially in this document:
[Gnome 3 System Settings changes]("https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB")

I want to hope they will integrate unity options inside the stock system settings applet of Gnome3.

as expected unity settings are going to be integrated in control center
[http://blog.didrocks.fr/post/Some-unity-configuration-in-gnome-control-center](http://blog.didrocks.fr/post/Some-unity-configuration-in-gnome-control-center).

---

