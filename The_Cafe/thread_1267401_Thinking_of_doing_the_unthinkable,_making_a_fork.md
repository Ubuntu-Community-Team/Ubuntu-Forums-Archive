---
title: "Thinking of doing the unthinkable, making a fork"
date: 2009-09-15
forum: The Cafe
---

### Post by curuxz on 2009-09-15
Hey guys,

Have not been around for...well a while... but I am back and now working from home again on my own company so have the time to be a bit more active in the community.

Today I upgraded (if you can call it that) to gimp 2.7 and I am really pissed. They have forced everyone now to save in XCF and moved all the other save features over to some export menu. Looking at their road map it seems like they have gone a bit mad. Instead of fixing things and improving what was one of my favorite FLOSS projects they are screwing around with the UI. The change from save to save and export is going to slow me down as a web professional who works with hundreds of images a day and they are continuing their path to changing to SDI when MDI is fine...it works?!


Despite being very busy I am so tempted to try making a fork, I am just disgusted at the response I got on one of their devs blog, being told to get my facts strait and read the spec, I had already done that and its insulting with this level of autocratic changes going into our software that actively make them less user friendly and productive.

Maybe I am alone in this, but I am interested to see what you all think?

---

### Post by HappinessNow on 2009-09-15
> **curuxz said:**
> Hey guys,

Have not been around for...well a while... but I am back and now working from home again on my own company so have the time to be a bit more active in the community.

Today I upgraded (if you can call it that) to gimp 2.7 and I am really pissed. They have forced everyone now to save in XCF and moved all the other save features over to some export menu. Looking at their road map it seems like they have gone a bit mad. Instead of fixing things and improving what was one of my favorite FLOSS projects they are screwing around with the UI. The change from save to save and export is going to slow me down as a web professional who works with hundreds of images a day and they are continuing their path to changing to SDI when MDI is fine...it works?!


Despite being very busy I am so tempted to try making a fork, I am just disgusted at the response I got on one of their devs blog, being told to get my facts strait and read the spec, I had already done that and its insulting with this level of autocratic changes going into our software that actively make them less user friendly and productive.

Maybe I am alone in this, but I am interested to see what you all think?
If you have the time, long term dedication, and know how then feel **free** to make a fork.

---

### Post by dragos240 on 2009-09-15
> **curuxz said:**
> Hey guys,

Have not been around for...well a while... but I am back and now working from home again on my own company so have the time to be a bit more active in the community.

Today I upgraded (if you can call it that) to gimp 2.7 and I am really pissed. They have forced everyone now to save in XCF and moved all the other save features over to some export menu. Looking at their road map it seems like they have gone a bit mad. Instead of fixing things and improving what was one of my favorite FLOSS projects they are screwing around with the UI. The change from save to save and export is going to slow me down as a web professional who works with hundreds of images a day and they are continuing their path to changing to SDI when MDI is fine...it works?!


Despite being very busy I am so tempted to try making a fork, I am just disgusted at the response I got on one of their devs blog, being told to get my facts strait and read the spec, I had already done that and its insulting with this level of autocratic changes going into our software that actively make them less user friendly and productive.

Maybe I am alone in this, but I am interested to see what you all think?


I agree with your thinking.

---

### Post by earthpigg on 2009-09-15
in this case, the fork would ***not*** mean effort that would have ***otherwise*** gone to developing GIMP due to the difference of opinion between you and the GIMP team.

so, go for it. GIMP has nothing to lose, and the community has everything to gain.

---

### Post by koleoptero on 2009-09-15
> **dragos240 said:**
> i agree with your thinking.

+1

---

### Post by starcannon on 2009-09-15
+1
@OP, was that at the Nabble boards? I kinda looked around to read your thread regarding the issue, and can't seem to locate it.

---

### Post by curuxz on 2009-09-15
> **&#20170 said:**
> If you have the time, long term dedication, and know how then feel to make a fork.

let me get this strait, I really do not want to have to spend time forking a project, esp not one as big and sucessful as the GIMP but they have totally lost sight of what is important. 

UI alterations are one thing, but actively carving up the work flow of a system, with no ability to change it (unless I am missing something and would be very glad to be proved wrong).

Linux and open source etc is meant to be about choice, but where is my choice, I use GIMP now for almost a decade and one day I wake up and instead of being open > work > save its open > work > save...no would you like to save as XCF, oh well I want export then...where was my choice?! whats my option? It even happens if you open a non-xcf file its literally a bare faced attempt to force all files to be worked in XCF, that means gimp is no longer an image editor, its an XCF editor.

I just don't understand when there was so much else to do why this was done, it will add about 10 awkward seconds on to each of my saves, and countless more time on non-xcf files i am working on. That adds up, thats just not in the spirit of what we are all trying to do by making life easier.

---

### Post by keiichidono on 2009-09-15
> **earthpigg said:**
> in this case, the fork would ***not*** mean effort that would have ***otherwise*** gone to developing GIMP due to the difference of opinion between you and the GIMP team.

so, go for it. GIMP has nothing to lose, and the community has everything to gain.

I agree. You might wanna look at Nathive though.

[1] [http://www.nathive.org/about/](http://www.nathive.org/about/)

---

### Post by HappinessNow on 2009-09-15
> **curuxz said:**
> let me get this strait, I really do not want to have to spend time forking a project, esp not one as big and sucessful as the GIMP but they have totally lost sight of what is important. 

UI alterations are one thing, but actively carving up the work flow of a system, with no ability to change it (unless I am missing something and would be very glad to be proved wrong).

Linux and open source etc is meant to be about choice, but where is my choice, I use GIMP now for almost a decade and one day I wake up and instead of being open > work > save its open > work > save...no would you like to save as XCF, oh well I want export then...where was my choice?! whats my option? It even happens if you open a non-xcf file its literally a bare faced attempt to force all files to be worked in XCF, that means gimp is no longer an image editor, its an XCF editor.

I just don't understand when there was so much else to do why this was done, it will add about 10 awkward seconds on to each of my saves, and countless more time on non-xcf files i am working on. That adds up, thats just not in the spirit of what we are all trying to do by making life easier.

EDIT: I left out an essential word;

> **&#20170 said:**
> If you have the time, long term dedication, and know how then feel **free** to make a fork.

btw: It would be nice if this fork included OpenSource software that has the functions of PhotoMatix, Lightroom 2 and/or Aperture not to mention has advanced features of CS4; but then that would be whole other projects like Raw Therapee (as in features like Lightroom 2 and Aperture) and such.

---

### Post by hessiess on 2009-09-15
> **curuxz said:**
> Hey guys,

Have not been around for...well a while... but I am back and now working from home again on my own company so have the time to be a bit more active in the community.

Today I upgraded (if you can call it that) to gimp 2.7 and I am really pissed. They have forced everyone now to save in XCF and moved all the other save features over to some export menu. Looking at their road map it seems like they have gone a bit mad. Instead of fixing things and improving what was one of my favorite FLOSS projects they are screwing around with the UI. The change from save to save and export is going to slow me down as a web professional who works with hundreds of images a day and they are continuing their path to changing to SDI when MDI is fine...it works?!


Despite being very busy I am so tempted to try making a fork, I am just disgusted at the response I got on one of their devs blog, being told to get my facts strait and read the spec, I had already done that and its insulting with this level of autocratic changes going into our software that actively make them less user friendly and productive.

Maybe I am alone in this, but I am interested to see what you all think?

If you are good enough at C to be able to maintain it then go ahead, I also hate the path that GIMP appears to be heading down, and may ditch it or stick with 2.6.

---

### Post by HappinessNow on 2009-09-15
Just don't make another GimpShop.

---

### Post by purgatori on 2009-09-15
If GIMP goes all the way with the single-window interface I may just end up using your fork :P

---

### Post by HappinessNow on 2009-09-15
> **purgatori said:**
> If GIMP goes all the way with the single-window interface I may just end up using your fork :P
Two forks are better then one spoon!

---

### Post by SunnyRabbiera on 2009-09-15
I dunno, having a "export" option can be helpful when starting new projects, do all initial work in xcf and later export when done.

---

### Post by aesis05401 on 2009-09-15
Forking would probably be a great experience from the development angle.  Have you already reached the limits of the plug-in architecture, though?  I know there are various file save plug-ins that allow complex operations through the PDB API.

I don't do image manipulation, but the intro plug-in tutorial looks easy:_[http://developer.gimp.org/writing-a-plug-in/1/index.html]("http://developer.gimp.org/writing-a-plug-in/1/index.html")_.

---

### Post by dragos240 on 2009-09-15
> **&#20170 said:**
> Just don't make another GimpShop.

I tried that. What's the difference?

---

### Post by Ric_NYC on 2009-09-15
Please... Please. Before starting another fork, please fix PulseAudio first.

---

### Post by dragos240 on 2009-09-15
> **Ric_NYC said:**
> Please... Please. Before starting another fork, please fix PulseAudio first.

-1, you need to just set it up correctly, but I want them to remove it from the default installation.

---

### Post by Warpnow on 2009-09-15
> **dragos240 said:**
> -1, you need to just set it up correctly, but I want them to remove it from the default installation.

Does set up = uninstall in this context?

---

### Post by coldReactive on 2009-09-15
Any screenshots you can show us of GIMP 2.7's new features? I'm not able to upgrade yet =/ And probably won't for a while.

Edit: Nevermind, I found a way to upgrade via PPA.

---

### Post by hessiess on 2009-09-15
> **SunnyRabbiera said:**
> I dunno, having a "export" option can be helpful when starting new projects, do all initial work in xcf and later export when done.

I do a lot of work on PNG images, if it forces saving in XCF without manual `exporting' it would be completely unusable. Even photoshop can save as formats besides PSD without any stupid `export' rubbish.

---

### Post by coldReactive on 2009-09-15
I also noticed that closing the big tools dialog doesn't close GIMP no more, this totally sucks. Doing so will cause GIMP to forget your panels that you added to the toolbox dialog.

---

### Post by 23meg on 2009-09-15
Why specifically a fork, when you can maintain a branch or patchset with your changes, or maybe implement them via a plugin?

---

### Post by NormanFLinux on 2009-09-15
You could call it Neobuntu... but Canonical says no no to any distro label that implies an association with them. NoobLinOS might pass the lawyers' nod.

---

### Post by Redundant Username on 2009-09-15
+1
I'm still on 2.6. I'm going to halt upgrades on Gimp now.

---

### Post by chessnerd on 2009-09-15
A fork as unthinkable? A fork is one of the best things about open source programs. If making a fork was considered "unthinkable" we wouldn't have Ubuntu or Slackware or Arch as they are all forks of Debian, SLS, and CRUX respectively. A fork is not something that should be discouraged, or thought of as "unthinkable," it should be embraced. A fork gives the opportunity for advancement and improvement. If you have the time and energy to create a GIMP fork then by all means, do so. 

I like the idea behind it and agree with your frustration. The GIMP should be expanding what formats it supports, not shrinking the number. The very concept is counter intuitive to the idea of gaining market share. Imagine if OpenOffice only supported saving to ODF formats in the next version and made everyone "export" to .doc instead of save natively in it? No one would use it as a replacement for Microsoft Office anymore and there goes well over half of their market.

So go out and make your fork and do what so many have done before you: make the world of FOSS a better place.

---

### Post by HappyFeet on 2009-09-15
I'm thinking of making a spoon.

---

### Post by DeadSuperHero on 2009-09-15
Has everyone forgotten the FunPidgin fork?

Fat lot of good that ever did. This is in the same logic.

---

### Post by -grubby on 2009-09-15
Sorry to be a party pooper here, but this seems like kind of a stupid reason to fork.

First off, it's not like they removed the ability to save as those formats altogether. I agree it's annoying, but not annoying enough to warrant a fork.

Secondly, as someone else said, a plugin to restore the old functionality is perfectly plausible.

Thirdly, have fun maintaining that new codebase yourself.

And lastly... er, I forgot. Maybe I'll come back later and fill it in.

---

### Post by CJ Master on 2009-09-16
> **chessnerd said:**
> A fork as unthinkable? A fork is one of the best things about open source programs. If making a fork was considered "unthinkable" we wouldn't have Ubuntu or Slackware or Arch as they are all forks of Debian, SLS, and CRUX respectively. A fork is not something that should be discouraged, or thought of as "unthinkable," it should be embraced. A fork gives the opportunity for advancement and improvement. If you have the time and energy to create a GIMP fork then by all means, do so. 

I like the idea behind it and agree with your frustration. The GIMP should be expanding what formats it supports, not shrinking the number. The very concept is counter intuitive to the idea of gaining market share. Imagine if OpenOffice only supported saving to ODF formats in the next version and made everyone "export" to .doc instead of save natively in it? No one would use it as a replacement for Microsoft Office anymore and there goes well over half of their market.

So go out and make your fork and do what so many have done before you: make the world of FOSS a better place.

While arch was inspired by Crux it wasn't actually forked from it.

---

### Post by MaxIBoy on 2009-09-16
[LIST=1]
[*]Agree about export not being the same as save, but it's not really that big a deal. It's offset pretty much entirely if you A) memorize the ctrl+E key combo and B) use xcf for all your in-progress work, which is a good idea anyway.
[*]The new interface will be **OPTIONAL**. You don't need to choose it if you like the old one. Repeat: The. New. Interface. Will. Be. Optional. You. Do. Not. Need. To. Choose. It. If. You. Don't. Want. To.
[/LIST]

---

### Post by NovaAesa on 2009-09-16
I have a feeling the OP wanted us to do the fork for him/her...

---

### Post by HappinessNow on 2009-09-16
> **HappyFeet said:**
> I'm thinking of making a spoon.

["There is No spoon"]("http://www.youtube.com/watch?v=YXKFTzlBziI")

---

### Post by Trail on 2009-09-16
> **curuxz said:**
> its insulting with this level of autocratic changes going into **_our_** software that actively make them less user friendly and productive.

Wait, what?

---

### Post by curuxz on 2009-09-16
> **MaxIBoy said:**
> 
[LIST=1]
[*]Agree about export not being the same as save, but it's not really that big a deal. It's offset pretty much entirely if you A) memorize the ctrl+E key combo and B) use xcf for all your in-progress work, which is a good idea anyway.
[*]The new interface will be **OPTIONAL**. You don't need to choose it if you like the old one. Repeat: The. New. Interface. Will. Be. Optional. You. Do. Not. Need. To. Choose. It. If. You. Don't. Want. To.
[/LIST]



If its OPTIONAL, how to I TURN IT OFF? 

The whole save/export thing represents only the tip of the ice burg, its just a particularly clear example of how this project seems to be very poorly managed at the moment. I just had this comment from one of their people when talking about this on his blog "So in your book GIMP should present inaccurate information (showing an XCF composition as saved when it is not) and then you call the users that trust this information stupid? Wow I'm glad you are not in charge of the future of the GIMP UI. You are right in that some old users are alienated with the new save+export, but not having a broken UI and fulfilling our product vision is more important than pleasing retrogressive old-timers...." they seem to acknowledge that its about people being so stupid as to think saving in a flat file format will be able to come back and work on layers, as I replied to him, all he would have to do is an information prompt on save, not destroy the save feature.

Export instead of save is so counter intuitive its unbelievable, you should be able to work on any format you chose, I agree in that its like Oo only working with ODT unless you export. The thing that makes it even more annoying is once you have chosen to export you cant quick export, you have to go through the whole thing each time. So, as I do many many times a day...open a file make a tweek...save and look at how it looks on my site...make another etc.... becomes very very tedious.


I only described forking as unthinkable because I hate when people fork for no good reason but it really does seem the direction of gimp has really lost its way and perhaps a 2.6 fork is a good idea for no other reason that to make another package in the repo's. Ie at the moment eventually everyone will be auto-upgraded to 2.7 at least if there was a static copy of 2.6 (like they do with firefox) then people could chose to stay on how it is now. Then improving my version would be a secondary goal if I could get enough help to make significant changes.

---

### Post by t0p on 2009-09-16
> **curuxz said:**
> .
  perhaps a 2.6 fork is a good idea for no other reason that to make another package in the repo's.

So now your hypothetical fork is going to be included in the repos?

Optimism is good.  Some code would be better.

---

### Post by curuxz on 2009-09-16
I am not sure yet, but there must be a way of making a frozen version of GIMP at 2.6.7 that can be installed in APT. I guess ill have to look it up, its not like I am asking anyone to do it for me I just wondered If its me alone that hates 2.7 and the direction of the project of if there are more people against where its going.

I guess I'll have to give things a go, although at this stage I want to shy away from making it a full blown fork since I have neither the time nor resources to make something that could compete with one of the oldest open source projects.

---

### Post by handy on 2009-09-16
> **chessnerd said:**
> If making a fork was considered "unthinkable" we wouldn't have Ubuntu or Slackware or Arch as they are all forks of Debian, SLS, and CRUX respectively.

Arch was made from LFS.

---

### Post by t0p on 2009-09-16
> **curuxz said:**
> at this stage I want to shy away from making it a full blown fork since I have neither the time nor resources to make something that could compete with one of the oldest open source projects.

So I add my voice to others, and ask: why not just a patch/plugin then?  It'd take up a lot less of your time, and judging from some of the comments here it might be popular.

---

### Post by handy on 2009-09-16
**@curuxz:**  If you can accomplish what you need with a plugin, it should save you a great deal of time.  You will only have to maintain the plugin as well.

***[Edit:]**  What he said. :lolflag:*

---

### Post by curuxz on 2009-09-16
ill have a look at the plugin system, see if it can be achieved that way, or via a patch

---

### Post by hessiess on 2009-09-16
> **t0p said:**
> So I add my voice to others, and ask: why not just a patch/plugin then?  It'd take up a lot less of your time, and judging from some of the comments here it might be popular.

Im not sure, but I doubt that they would export enough options into the plug-in API to allow you to completely change how image saving works.

---

### Post by handy on 2009-09-16
> **hessiess said:**
> Im not sure, but I doubt that they would export enough options into the plug-in API to allow you to completely change how image saving works.

So a patch would be possible?

---

### Post by ceti331 on 2009-09-16
Does 2.7 get the airbrush size-pressure control the right way round :)
this is a minor change i'm after

---

### Post by anaconda on 2009-09-16
> **curuxz said:**
> Hey guys,
 changes going into our software that actively make them less user friendly and productive.


How could they make gimp LESS user friendly?  I thought that it was already as un-userfriendly as possible.

Have you ever tried krita?
(

---

### Post by Fri13 on 2009-09-16
> **CJ Master said:**
> While arch was inspired by Crux it wasn't actually forked from it.

[http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg](http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg)

Under and middle of SUSE timeline you can find both.

There are few main distributions of Linux OS from what has used to fork multiple other distributions. All using at least Linux OS and most of them some of main system parts from GNU.

---

### Post by saulgoode on 2009-09-16
> **curuxz said:**
> Export instead of save is so counter intuitive its unbelievable, you should be able to work on any format you chose, I agree in that its like Oo only working with ODT unless you export. The thing that makes it even more annoying is once you have chosen to export you cant quick export, you have to go through the whole thing each time.
I believe you have misunderstood the [specification](http://gui.gimp.org/index.php/Save_%2B_export_specification). If you open a non-XCF file, edit it, and then the *first time* you export it, you should be presented with a dialog which is properly configured to save it back under the same name and using the same format and options. Subsequent exports will be saved *with no prompting whatsoever* through use of the "Export to <filename>" menu function. 

Note that this is, in many cases, an improvement over the current workflow of re-saving your file after editing. If you have made any changes which are not supported by the file format (such as adding text or other layers, adding an alpha channel, or changing the image mode/colordepth), current versions of GIMP will **always** present an "export dialog" and require you to specify how those unsupported features are to be handled. You are correct that currently GIMP does permit saving to the same file *as long as no edits result in unsupported features*.

> **curuxz said:**
> So, as I do many many times a day...open a file make a tweek...save and look at how it looks on my site...make another etc.... becomes very very tedious.
If you are using a lossy file format such JPEG, GIF, or indexed-color PNG then your approach is not a very good one, as each time you edit your file, the image quality is degraded. If instead, you save your file in the lossless XCF format, and only save your "exported" version when it is needed, then you avoid this degradation. You also retain all the features from previous editing sessions such as separate layers, masks, saved selections, paths, and vector graphics (GFIG). In the future (which is one of the motivations for these changes), support will be provided for GEGL operations (what Photoshop has somewhat implemented as "adjustment layers") as well as acyclic directed graphing structures.

If you are not using a lossy file format, then no export dialog will be presented. If you are using a lossy file format, the export dialog only needs to be presented the first time. 

> **curuxz said:**
> I only described forking as unthinkable because I hate when people fork for no good reason but it really does seem the direction of gimp has really lost its way...
You are, of course, free to fork GIMP. If you choose to do so, I would recommend doing so under a name that will avoid any confusion with the GIMP project. 

> **ceti331 said:**
> Does 2.7 get the airbrush size-pressure control the right way round :)
this is a minor change i'm after
GIMP's airbrush attempts to mimic a real airbrush: the closer your tool is to the surface (i.e., the harder you press), the smaller the region is that gets painted. Some would consider this "the right way round". :)

---

### Post by hessiess on 2009-09-16
> **handy said:**
> So a patch would be possible?

yes.

> 
If you are using a lossy file format such JPEG, GIF, or indexed-color PNG then your approach is not a very good one, as each time you edit your file, the image quality is degraded. If instead, you save your file in the lossless XCF format, and only save your "exported" version when it is needed, then you avoid this degradation. You also retain all the features from previous editing sessions such as separate layers, masks, saved selections, paths, and vector graphics (GFIG). In the future (which is one of the motivations for these changes), support will be provided for GEGL operations (what Photoshop has somewhat implemented as "adjustment layers") as well as acyclic directed graphing structures.


I use a simmaler work flow and if you are using a lossless format like bog standard RGBA PNG it is not a problem, Formats like GIF and Jpeg are useless for most image editing work as they are lossy and don't support alpha transparency. . btw JPEG is only meant to be used for compressing digital photographic data, not general images.

---

### Post by madjr on 2009-09-16
> **anaconda said:**
> How could they make gimp LESS user friendly?  I thought that it was already as un-userfriendly as possible.

Have you ever tried **krita**?
(

+1 for Krita

i was thinking about starting with Gimp, but i might ditch that and go with Krita

what you guys think?

the only downside for us beginners is not enough video tutorials, while gimp has tons

---

### Post by handy on 2009-09-16
> **Fri13 said:**
> [http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg](http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg)

Under and middle of SUSE timeline you can find both.

There are few main distributions of Linux OS from what has used to fork multiple other distributions. All using at least Linux OS and most of them some of main system parts from GNU.

The image you posted a link to is unfortunately in error.  Following is a quote from [**_this page of the Arch wiki_**]("http://wiki.archlinux.org/index.php/Arch_Compared_To_Other_Distros"):

[I]Judd Vinet built Arch from scratch, and then wrote pacman in C. Arch is sometimes, therefore, humorously described simply as "Linux, with a nice package manager."

Arch vs CRUX

    * Q: Is Arch Based on CRUX?
    * A: No. Arch is independently developed, was built from scratch and is not based on any other GNU/Linux distribution. [/I]

---

### Post by chessnerd on 2009-09-17
> **handy said:**
> The image you posted a link to is unfortunately in error.  Following is a quote from [**_this page of the Arch wiki_**]("http://wiki.archlinux.org/index.php/Arch_Compared_To_Other_Distros"):

[I]Judd Vinet built Arch from scratch, and then wrote pacman in C. Arch is sometimes, therefore, humorously described simply as "Linux, with a nice package manager."

Arch vs CRUX

    * Q: Is Arch Based on CRUX?
    * A: No. Arch is independently developed, was built from scratch and is not based on any other GNU/Linux distribution. [/I]

From en.wikipedia.org/wiki/Arch_Linux, "Inspired by CRUX, another minimalist distribution, Judd Vinet started Arch Linux in March 2002."

So it was a fork of CRUX, or based on CRUX, but was inspired by CRUX in a similar way that Linux was inspired by Minix. I was in error in saying that Arch was a fork of CRUX, and I apologize. I've only used Arch a couple of times and I didn't know much about it's history except that it was similar to CRUX (I was told "based on CRUX" somewhere, but I guess that person was in error). I was simply trying to come up with a list of three big name forks and I thought that Arch rounded out the list well. I could have gone with Linux Mint being a fork of Ubuntu or CentOS being a fork of Red Hat, but I though of the CRUX/Arch one and went with that.

Almost all Linux distros branched off from a larger one originally. In fact, the list of "original" or "unique" distros is very small nowadays. I think Debian and Red Hat are pretty much the only ones left. Even SuSE was originally a German translation of Slackware that broke off and became a commercial distribution. My point was only that forking in the world of open source happens all the time and should always be embraced as a good thing and never discouraged because the worst that can happen is that the fork dies, but the best that can happen is that the fork surpasses the quality of the original and we are left with a stronger, better program that we can all gain something from. This is what happened with Slackware and SLS and some argue that this has happened with Ubuntu and Debian, although Debain, unlike SLS, is still standing strong after the fork. Also,Debian has a different audience than Ubuntu, unlike with CentOS and Red Hat where the audience is the same. 

A fork of the GIMP is something that I would welcome and I hope that the saving mechanism isn't the only thing that's changed if a fork happens. I would like the see a GIMP where everything is made simpler and easier to use. A GIMP where you can sit anyone down in front of it and they can instantly figure out how at least the basic things work. Also, I would like to point out that this is not the first time a minor fork of the GIMP was created. Look at GIMPShop. Only one thing was changed: a window around the toolboxes was added so that the whole program exists inside one box. That's it. It's not a huge difference, but it's a nice one, in my opinion, because I don't like having to deal with three windows for one program. Some people like the GIMP's model and so those people use the GIMP, those that don't can use GIMPShop. If a fork is made from this, those that like the export idea can use the GIMP and those that don't can use (insert name of fork). 

As for the name, I think I've got a good one: GPS - GNU Picture Software or GNU Production Software. Why GPS? It can have the slogan: "Moving in the Right Direction" to denote the fact that it is moving towards better usability than the GIMP. What do you think?

---

### Post by handy on 2009-09-17
Yes, Arch is not a fork of any other Linux.  Crux was inspirational, but it was not used in any way to make Arch.

Arch was built from scratch.

---

