---
title: "allmyapps.com an appstore with cool features for Ubuntu Linux"
date: 2009-07-16
forum: The Cafe
---

### Post by thibs on 2009-07-16
I just wanted to let you know of [allmyapps.com]("http://allmyapps.com"), a site we've launched with a friend of mine earlier this year. We did not communicate much so far as we thought it was not yet ready... but it's getting better everyday and we think it is now in a cool enough state for us to begin evangelize a bit more :)

Basically we wanted to provide new Ubuntu users (read: "with no specific Linux / FOSS knowledge") with a website that would allow them to find and install new apps on their system in a cool and user-friendly way. This is why we tried to focus hard on eye-candy and usability (do not hesitate to tell us if you think we failed here or, better, if you have any improvement suggestions!).

1 click installation is provided through apt-url so it is completely safe for anybody to use. As we depend directly from the official repositories, you will not find malicious apps on allmyapps. We will soon register some apps from some specific external repositories (like medibuntu or goole) but that's about it. For these specific apps, it will be up to the user to decide whether he wants to add the 3rd party repositories or not.

Besides application discovery, we intend to provide a whole range of cool features for allmyapps users. The first one that we began implementing is the ability to save a list of your favorite applications and install them in 1 click (well a bit more if you count the required apt-url clicks). This way you can save your apps online (maybe I should say "in the cloud" to sound more trendy) and install them anytime you wish. And in the next release, you'll be able to export and share this list of applications.

Of course, many functionalities covered by allmyapps are covered by desktop tools like synaptic, "add/remove..." or the future AppCenter... but we think that taking a web centric approach allows us to complement these tools nicely.

Maybe the best thing would be that you try it out by yourself to see what it looks like: [http://allmyapps.com](http://allmyapps.com) 

Of course, don't hesitate to tell us what you think!

PS1: Kubuntu users need to install apt-url as it is not installed by default on Kubuntu
PS2: Non firefox users must have the apt:// handler registered and connected to apt-url in their web browser for the 1 click installation to work
PS3: Users of a non official Firefox 3.5 build, see PS2!

---

### Post by Jimleko211 on 2009-07-16
This is a really cool site, I'm definitely going to try it out.

---

### Post by Jimleko211 on 2009-07-16
Unforutantely, I already found a bug.  I tried to install Supertux on your site, and it told me that it only worked on 8.04, 8.10, and 9.04.  I'm running Swiftfox 3.5, and I've already checked that apt:// is opened with the apt-url application.

---

### Post by lovinglinux on 2009-07-16
I like the idea of "My List". I use a script to generate the list of installed applications when re-installing Ubuntu or installing a new release, but this definitely could make life easier for newcomers.

BTW, would be nice if you could import a user generated script into "My List". 

To create the list:

```
dpkg --get-selections > ~/my-packages
```

To install applications from the list:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

---

### Post by mjitkop on 2009-07-16
I do find it interesting and I will be using it for testing purposes at this time. In the long term, I could see it built in Ubuntu. ;)

---

### Post by cariboo on 2009-07-16
Web sites like this will become redundant once the new [Appcenter]("https://wiki.ubuntu.com/AppCenter/") becomes available.

---

### Post by lovinglinux on 2009-07-16
> **Jimleko211 said:**
> Unforutantely, I already found a bug.  I tried to install Supertux on your site, and it told me that it only worked on 8.04, 8.10, and 9.04.  I'm running Swiftfox 3.5, and I've already checked that apt:// is opened with the apt-url application.

Me too. I'm using Firefox 3.5 compiled from source.

---

### Post by orion1315 on 2009-07-16
lol i thought the little thing on the right said facebook
But yea this looks rly cool ill try it out, keep up the good work!

Edit: 
            @Web sites like this will become redundant once the new [Appcenter]("https://wiki.ubuntu.com/AppCenter/") becomes available.
get ur negativity outa here :D

---

### Post by Waappu on 2009-07-16
Hi

Layout of site is very nice. But because I do not understand fully all security risks and so on, I would not let any site install anything to my pc.

---

### Post by thibs on 2009-07-16
Thanks everybody for your feedbacks!

@lovinglinux @Jimleko211 : I investigated why it failed with you. Actually, to determine if the user who clicks on "Install" is on Ubuntu or not, we look for the string 'ubuntu' in the web browser user agent. Swiftfox and Firefox 3.5 do not have it so far so allmyapps thinks you're not running ubuntu... I guess we could add an option for registered users to explicitely ask to bypass this check.

@lovinglinux : the import of user generated list is a good idea... I put it in our todo list (which is unfortunately already a bit long :/ ).

---

### Post by Jimleko211 on 2009-07-16
> **thibs said:**
> Thanks everybody for your feedbacks!

@lovinglinux @Jimleko211 : I investigated why it failed with you. Actually, to determine if the user who clicks on "Install" is on Ubuntu or not, we look for the string 'ubuntu' in the web browser user agent. Swiftfox and Firefox 3.5 do not have it so far so allmyapps thinks you're not running ubuntu... I guess we could add an option for registered users to explicitely ask to bypass this check.


Cool, thank you.  I hope that this site doesn't become obsolete because of AppCenter, though I do think it'll become useful for installing software from other PPAs.

---

### Post by lovinglinux on 2009-07-16
> **thibs said:**
> @lovinglinux @Jimleko211 : I investigated why it failed with you. Actually, to determine if the user who clicks on "Install" is on Ubuntu or not, we look for the string 'ubuntu' in the web browser user agent. Swiftfox and Firefox 3.5 do not have it so far so allmyapps thinks you're not running ubuntu... I guess we could add an option for registered users to explicitely ask to bypass this check.

Changing the user agent with [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59) extension does work.


> **thibs said:**
> @lovinglinux : the import of user generated list is a good idea... I put it in our todo list (which is unfortunately already a bit long :/ ).

You could provide a service like [XMarks](https://addons.mozilla.org/en-US/firefox/addon/2410) for Ubuntu packages ;) It wouldn't be hard to make a Firefox extension that could generate the package selections, download the user list from your site and merge them.

What about Packagemarks? :)

---

### Post by thibs on 2009-07-16
@lovinglinux I did not know about XMarks (actually I still don't as I cannot go see their website as the proxy we have here thinks it contains erotic content :)). I'm not sure how hard it would be to implement the Firefox extension you describe... it might be harder than you'd think as it would need to be a plug-in (to interact with the user system) and not a simple extension (which is confined into the web browser). I'll investigate it, thanks for the suggestion!

---

### Post by Simian Man on 2009-07-16
Good job, really professional looking site.

> **cariboo907 said:**
> Web sites like this will become redundant once the new [Appcenter]("https://wiki.ubuntu.com/AppCenter/") becomes available.

Well I'd guess you have at least about 3 years then :).

---

### Post by lovinglinux on 2009-07-16
> **thibs said:**
> @lovinglinux I did not know about XMarks (actually I still don't as I cannot go see their website as the proxy we have here thinks it contains erotic content :)). I'm not sure how hard it would be to implement the Firefox extension you describe... it might be harder than you'd think as it would need to be a plug-in (to interact with the user system) and not a simple extension (which is confined into the web browser). I'll investigate it, thanks for the suggestion!

Actually, I'm creating one already ;)

Basic functionality tho.

---

### Post by Cheesemill on 2009-07-16
> **Waappu said:**
> Hi
 
Layout of site is very nice. But because I do not understand fully all security risks and so on, I would not let any site install anything to my pc.
 
This site is basically just another front-end for apt-get (like Synaptic).
It only uses the official repos so the security risk is exactly the same as using Add/Remove Programs - Zero.

---

### Post by zekopeko on 2009-07-16
> **Waappu said:**
> Hi

Layout of site is very nice. But because I do not understand fully all security risks and so on, I would not let any site install anything to my pc.

you probably missed the part were the OP said that the links only point to the applications in the default/offical UBUNTU repositories. this web site is simply a web frontend to apt-get just like synaptic is a GTK frontend to apt-get.

---

### Post by earthpigg on 2009-07-16
hi,

using ff 3.5 (aka 'shiretoko'), from the official ubuntu repos, your website does not work.

i am certain that i can do a bunch of reasearch to figure it out for myself but, like most of your potential viewers, i have a very short attention span. just enough span to make this post since i happen to already be logged into ubuntuforums.org.

i suggest plastering a 'FAQ: how to make this work!!' link all over the damn place. :D

---

### Post by lovinglinux on 2009-07-16
> **earthpigg said:**
> hi,

using ff 3.5 (aka 'shiretoko'), from the official ubuntu repos, your website does not work.

i am certain that i can do a bunch of reasearch to figure it out for myself but, like most of your potential viewers, i have a very short attention span. just enough span to make this post since i happen to already be logged into ubuntuforums.org.

i suggest plastering a 'FAQ: how to make this work!!' link all over the damn place. :D

Until the OP updates the site, use [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59) extension.

---

### Post by thibs on 2009-07-17
> **earthpigg said:**
> hi,
i suggest plastering a 'FAQ: how to make this work!!' link all over the damn place. :D

You're right, we definitely need a FAQ. I'll try to have a first shot for the next release, the problem is that writing correctly takes more time than coding correctly ;)

---

### Post by hyperdude111 on 2009-07-17
We already have getdeb

---

### Post by lovinglinux on 2009-07-17
> **hyperdude111 said:**
> We already have getdeb

Not the same. GetDeb provides new releases, usually not available in the repositories, while allmyapps provides a list of packages in the repositories, allowing to install them all at once.

---

### Post by Bou on 2009-07-17
Up to yesterday I would have voted for the second option, "it can be useful to some people". Today, since it supports install lists, I've changed to the first: "definitely, I'll be using it myself".

Basically you log in and have a list of your favourite apps, which you can install with 1 click.

2 Gripes I'm having with allmyapps:

-It still does not support Karmic, which I use. But oh well.
-I would like to be able to UNINSTALL apps which I don't want with the same click that installs my favourite apps. I realize that's an apturl limitation, but It would save me the visit to Synaptic after a fresh install.

---

### Post by thibs on 2009-07-17
> **Bou said:**
> Up to yesterday I would have voted for the second option, "it can be useful to some people". Today, since it supports install lists, I've changed to the first: "definitely, I'll be using it myself".

Great :D

> **Bou said:**
> 
2 Gripes I'm having with allmyapps:

-It still does not support Karmic, which I use. But oh well.
-I would like to be able to UNINSTALL apps which I don't want with the same click that installs my favourite apps. I realize that's an apturl limitation, but It would save me the visit to Synaptic after a fresh install.

Good points. Karmic support will come as soon as Karmic repostory freezes. For Jaunty, we did it a bit earlier so we had to resynchronize with the repository afterwards. We'll try to avoid having to do this this time...

Concerning application uninstallation, as we rely on apt-url we're indeed limited by its functionality today. Once we reach a satisfying level of functionality on allmyapps, we will probably help with apt-url development so that it becomes more feature complete.

@lovinglinux thanks for answering to @hyperdude111. You are right: getdeb and allmyapps pursue very different objectives: Getdeb provides you with new packages (which are not available in the officials repos) while allmyapps wants to make it easier to find and install packages that are provided in the official repositories.

---

### Post by Bou on 2009-07-17
Also, thibauld: do you think that the featured applications slideshow could stop if you hover the cursor over it? It's quite difficult to read the description and click the install button, the app changes before you can finish.

Maybe two small buttons "previous / next" could appear in a corner, to allow you to browse featured applications at your own pace. If you move the cursor out of the area, the slideshow starts again. How would that be?

By the way, how can one get an app they like in the featured apps slideshow? Maybe write a review and take a screenshot? I'm sure that would encourage folks to participate.

---

### Post by Bou on 2009-07-17
Oh! I also wanted to suggest a couple things about the interface:

-when you hover the cursor over a button, it looks concave instead of convex, and that detracts from the impression of it being a "solid" thing. I think other ways to highlight the button would look better (quick mockups attached).

-The filter box does not use the GTK widgets. Could that be fixed?

Thanks again for your work thibauld.

---

### Post by binbash on 2009-07-17
> **cariboo907 said:**
> Web sites like this will become redundant once the new [Appcenter]("https://wiki.ubuntu.com/AppCenter/") becomes available.

I agree with this.

---

### Post by sertse on 2009-07-17
App center will come when new theme comes. ;)

---

### Post by 3rdalbum on 2009-07-17
Very cool site... very very cool. Nice and professional, except for the mistake in the description for Frozen Bubble ("one of the coolest Linux game out there").

---

### Post by thibs on 2009-07-17
> **Bou said:**
> Also, thibauld: do you think that the featured applications slideshow could stop if you hover the cursor over it? It's quite difficult to read the description and click the install button, the app changes before you can finish.

I agree that the slideshow is a bit broken right now... We'll fix it for the next release! Concerning, the featured apps, it's an interesting idea: the user could for example write a review of an app and tick a "propose as featured app" check box.

For the buttons and the concave / convex thing, I hadn't noticed but it does not shock me much. Concerning the filter box, I'm afraid there's nothing I can do here.

@3rdalbum: is the mistake with my english or with the fact that, in your opinion, Frozen Bubble is not one of the coolest game ? :)

---

### Post by Ms_Angel_D on 2009-07-17
Nice site, a couple of things though. Why does your site require my last name? Also I received the confirmation email but was told the code was invalid when I clicked the link.

---

### Post by Firestem4 on 2009-07-17
This is a great website..I haven't tried to use it but ive just been looking around. I have to say one of the things I like are the screenshots of many of the applications.

Great job!

---

### Post by thibs on 2009-07-17
> **Ms_Angel_D said:**
> Nice site, a couple of things though. Why does your site require my last name? Also I received the confirmation email but was told the code was invalid when I clicked the link.

I must admit we did not think that asking for a lastname would be an issue... feel free to put anything else in there if you want to :) Concerning the confirmation email, it's weird as nobody else reported a problem here. Could you please msg me with the confirmation link you got? This way, I'll be able to track the origin of the pb! thanks

---

### Post by lovinglinux on 2009-07-17
I just want to let you know that I have already developed the extension for Firefox, including search integration with allmyapps. It is not what I thought initially, but I think it could be useful.

The extension basically creates a list of installed packages and display them on a sidebar, so you can click them to open allmyapps using a search string for the selected app.

It also make backups of the list of installed applications and allow to batch install them after a clean install. All you have to do is to preserve the firefox profile. You can also export the list to run it with a command manually on another machine.

I will upload it as soon as I finish the basic features.

I have called it UMarks

Here are some screenshots

---

### Post by thibs on 2009-07-18
> **lovinglinux said:**
> I just want to let you know that I have already developed the extension for Firefox, including search integration with allmyapps. It is not what I thought initially, but I think it could be useful.

The extension basically creates a list of installed packages and display them on a sidebar, so you can click them to open allmyapps using a search string for the selected app.

It also make backups of the list of installed applications and allow to batch install them after a clean install. All you have to do is to preserve the firefox profile. You can also export the list to run it with a command manually on another machine.

I will upload it as soon as I finish the basic features.


UMarks looks really cool! I can't wait to try it out! Let me know once you've uploaded it so that I can be one of your first beta tester :)

---

### Post by lovinglinux on 2009-07-18
> **thibs said:**
> UMarks looks really cool! I can't wait to try it out! Let me know once you've uploaded it so that I can be one of your first beta tester :)

No problem. I will send you first via PM.

---

### Post by lovinglinux on 2009-07-18
The extension is available at [https://addons.mozilla.org/en-US/firefox/addon/13153/](https://addons.mozilla.org/en-US/firefox/addon/13153/)

Please test it and give some feedback.

---

### Post by UbuWu on 2009-07-18
Very nice site, but I like the clean layout of [AppNr.com]("http://appnr.com/") better.

---

### Post by Arup on 2009-07-19
Excellent, very easy to use for a first timer.

---

### Post by lovinglinux on 2009-07-19
> **lovinglinux said:**
> The extension is available at [https://addons.mozilla.org/en-US/firefox/addon/13153/](https://addons.mozilla.org/en-US/firefox/addon/13153/)

Please test it and give some feedback.

New version is available at [Mozilla Add-on site](https://addons.mozilla.org/en-US/firefox/addon/13153)

Now it also provides a search plug-in generator button in the preferences dialog, that will update your search bar plug-ins list with 6 more plug-ins: allmyapps.com, appnr.com, getdeb.net, launchpad.net, linuxappfinder.com and ubuntuforums.org

---

### Post by Ms_Angel_D on 2009-07-20
> **thibs said:**
> I must admit we did not think that asking for a lastname would be an issue... feel free to put anything else in there if you want to :) Concerning the confirmation email, it's weird as nobody else reported a problem here. Could you please msg me with the confirmation link you got? This way, I'll be able to track the origin of the pb! thanks

PM Sent ;)

---

### Post by earthpigg on 2009-07-21
heads up, mentioned your project in a relevant thread:

[http://ubuntuforums.org/showthread.php?t=1218778](http://ubuntuforums.org/showthread.php?t=1218778)

---

### Post by Jimleko211 on 2009-07-21
As a note, allmyapps.com does not support the Epiphany browser, either.

---

### Post by tom66 on 2009-07-21
Some things:

[list]
[*] On home page, you need to wait longer between the slides.
[*] On home page, you need to make the description box only slightly translucent. It makes it hard to read sometimes. 
[/list]

That's all for now... but looks like a neat site.

---

### Post by thibs on 2009-07-22
> **lovinglinux said:**
> New version is available at [Mozilla Add-on site](https://addons.mozilla.org/en-US/firefox/addon/13153)

Now it also provides a search plug-in generator button in the preferences dialog, that will update your search bar plug-ins list with 6 more plug-ins: allmyapps.com, appnr.com, getdeb.net, launchpad.net, linuxappfinder.com and ubuntuforums.org

I installed and tested version 0.1 and I wanted to test version 0.2 before giving you my feedback but unfortunately, there is a problem with version 0.2 which prevents it from being installed! Firefox issues the following message when trying to install UMarks 0.2 :

```
Firefox n'a pas pu installer le fichier situé à 
https://addons.mozilla.org/en-US/firefox/downloads/file/59395/umarks-0.0.2-fx-linux.xpi?confirmed?confirmed
raison : Hachage invalide sur le fichier (corruption possible du téléchargement)
-261

```
Which basically means in english:
```
Firefox could not install the file located at
https://addons.mozilla.org/en-US/firefox/downloads/file/59395/umarks-0.0.2-fx-linux.xpi?confirmed?confirmed
reason : Invalid hash on file (possible download corruption)
-261

```

UMarks version 0.1 installed flawlessly on my system (even without doing the chmod you recommend). My apps were detected withtout any problem... cool :) It was a bit weird to have to reload the window to see my apps appear but as you warn users to do so, it wasn't much of a problem. The integration with the different websites is great. I thought I could provide you with an api to get directly to a package's page instead of doing a search ? It would make sense no ? I did not test any further as I saw that version 0.2 was out. I tried to install it and got the problem described above. If you could fix it, I would continue testing!
cheers,

---

### Post by lovinglinux on 2009-07-22
> **thibs said:**
> I installed and tested version 0.1 and I wanted to test version 0.2 before giving you my feedback but unfortunately, there is a problem with version 0.2 which prevents it from being installed! Firefox issues the following message when trying to install UMarks 0.2 :

It seems to a problem created by the process of uploading to Mozilla site. The file installs locally, but not from Mozilla. I will replace it soon with version 0.0.3. Thanks.

> **thibs said:**
> UMarks version 0.1 installed flawlessly on my system (even without doing the chmod you recommend).

That's good news :)

> **thibs said:**
> It was a bit weird to have to reload the window to see my apps appear but as you warn users to do so, it wasn't much of a problem. 

This is something I still need to figure out. I have the same problem on another extension and I'm rewriting the entire code now. So this might take a while.

> **thibs said:**
>  The integration with the different websites is great. I thought I could provide you with an api to get directly to a package's page instead of doing a search ? It would make sense no ? I did not test any further as I saw that version 0.2 was out. I tried to install it and got the problem described above. If you could fix it, I would continue testing!
cheers,

An API would be great. I just notice that the address of the application is [http://www.allmyapps.com/app/](http://www.allmyapps.com/app/)*packagename*. If the package name in the url is exactly as the one we use to install via apt-get, then you don't need to provide an API. I just need to use that url instead of the search. Could you please confirm that?

Version 0.0.2 is attached. Download it and rename it to **.xpi** instead of **.zip** and then open it from Firefox. I will soon upload a new version to Mozilla.

---

### Post by thibs on 2009-08-07
@tom66 We've just put a new version of allmyapps online. Like you advised, I took care of making the slideshow slower and white tongue less translucent

@jimleko211 You should now be able to install even with epiphany (as long as you have apt-url registered as a handler for apt: links). You may get a warning message but it will not prevent you from installing apps

@earthpigg thanks :)

As usual, any addtional feedback is greatly appreciated!

---

