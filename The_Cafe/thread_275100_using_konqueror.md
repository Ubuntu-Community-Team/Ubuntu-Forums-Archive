---
title: "using konqueror"
date: 2006-10-10
forum: The Cafe
---

### Post by maniacmusician on 2006-10-10
I've tried both konq and all the fox's/weasel's and have to say that I really like konqueror. However, I have a couple of problems with it....

primarily, extensions. At one point, a user posted on the forums that it was possible to use ff extensions in konqueror [http://ubuntuforums.org/showthread.php?p=1520794#post1520794](http://ubuntuforums.org/showthread.php?p=1520794#post1520794) but i have never heard back from him (and kdeaddons.org doesnt exist) but if what he was saying was true, can someone point me in the right direction? If i could just have my precious google notebook extension. I also like AdBlock and DownThemAll but those aren't critical or anything. Google notebook is a must have forme. So if someone could point out how to get this done, i'd be grateful.

secondly, one thing that's been bugging me. Whenever I go to system places (icon) > Home, the items in konqueror show up in "icon view" and i have to change them to "detailed view" everytime. Does anyone know how to make detailed view stick? it's kind of a pain.

thanks

---

### Post by raublekick on 2006-10-10
i have the same concerns as you almost. i really want down them all or something similar. and also it always opens in widescreen size for me, and it never keeps the size that i resize it to, like firefox does.

---

### Post by slimdog360 on 2006-10-10
> **maniacmusician said:**
> 
secondly, one thing that's been bugging me. Whenever I go to system places (icon) > Home, the items in konqueror show up in "icon view" and i have to change them to "detailed view" everytime. Does anyone know how to make detailed view stick? it's kind of a pain.
settings-->save view profile "profile management". from here you can also save the window size

---

### Post by raublekick on 2006-10-10
well i'll be... thanks!

---

### Post by Bloodfen Razormaw on 2006-10-10
No, you can't use Gecko extensions in Konqueror.  Whoever told you that was mistaken.  They depend on XUL.  Thankfully, Konqueror doesn't use XUL.  Most of what people install extensions for is supported in Konqueror out of the box though, plus much more that extensions don't match.  There are extensions, available in the kdeaddons module for some added features for both web browsing and icon views.

As for the icon view problems, try saving your session after changing your icon view.  If you want Konqueror to not keep a default icon view for your profile, open the profile's file in ~/.kde/share/apps/profiles/<filename>, find the line with the konq_<whatever>view and delete it.  After I did that it uses whatever the last one you used was.

---

### Post by maniacmusician on 2006-10-10
yes, thank you very much! now if someone could just tell me about those extensions...i'd be all over konqueror over heartbeat 

i'll fix my flash issues later lol.

---

### Post by lzfy on 2006-10-10
Well I like konq. too but I have also some view problems. It doesn't remember the view options for each folder. I want some folders in detailed view and other in icon view, which is no problem in Explorer/Nautilus/Finder, but it doesn't work in konqueror.

---

### Post by kerry_s on 2006-10-10
He might have been thinking kde-apps( [http://kde-apps.org/](http://kde-apps.org/) ).

 "I also like AdBlock and DownThemAll"

It has adblock already just turn it on. You can grab a list and import it into konqueror.

For downloads you can try kget, i've never used downthemall so i'm not sure if it provides all the functions you need.

"the items in konqueror show up in "icon view" and i have to change them to "detailed view" everytime. Does anyone know how to make detailed view"

After you make your changes you have to save the profile(settings> save view profile).

I'll export my adblock list and try and attach it.->

---

### Post by maniacmusician on 2006-10-10
> **Bloodfen Razormaw said:**
> No, you can't use Gecko extensions in Konqueror.  Whoever told you that was mistaken.  They depend on XUL.  Thankfully, Konqueror doesn't use XUL.  Most of what people install extensions for is supported in Konqueror out of the box though, plus much more that extensions don't match.  There are extensions, available in the kdeaddons module for some added features for both web browsing and icon views.

As for the icon view problems, try saving your session after changing your icon view.  If you want Konqueror to not keep a default icon view for your profile, open the profile's file in ~/.kde/share/apps/profiles/<filename>, find the line with the konq_<whatever>view and delete it.  After I did that it uses whatever the last one you used was.
already got the saving the view thing from slimdog. But it's a damn shame that i cant use my extensions. if you follow that link in my first post, the guy was pretty sure about what he was talking about. he said that firefox extensions dont usually use XUL and that people can write a script to make them usable in konqueror...I dunno, what he said made sense. But perhaps it was only science fiction.

:'( but i like konqueror so much..

---

### Post by maniacmusician on 2006-10-10
> **kerry_s said:**
> He might have been thinking kde-apps( [http://kde-apps.org/](http://kde-apps.org/) ).

 "I also like AdBlock and DownThemAll"

It has adblock already just turn it on. You can grab a list and import it into konqueror.

For downloads you can try kget, i've never used downthemall so i'm not sure if it provides all the functions you need.

"the items in konqueror show up in "icon view" and i have to change them to "detailed view" everytime. Does anyone know how to make detailed view"

After you make your changes you have to save the profile(settings> save view profile).

I'll export my adblock list and try and attach it.->
i added it. dont really know if it worked (there was already a list in there. I just imported yours). 

Really, the most important extension for me is google notebook. and SoundMachine said that it's just a combination of XML, HTML, and javascript, thus it can be used in Konqueror. and its really the only thing I care about taking to konqueror.

---

### Post by raublekick on 2006-10-10
kget is not a good replacement for downthemall. the only useful thing i can get kget to do is queue up downloads that i manual click the links for.

---

### Post by Bloodfen Razormaw on 2006-10-10
It almost certainly has at least some XUL component.  Many Firefox extensions could probably be ported trivially to Konqueror, but I doubt there are any Firefox extensions that you could download and have just work in Konqueror (unless it were to actually be a standard Netscape plugin).

---

### Post by maniacmusician on 2006-10-10
ah yeah DownThemAll is a really cool extension, KGet can't compare. Though all I really use DTA for is when I have a webpage with lots of images that I want to download. Just right click, DownThemAll, set the filter for Images, and click Start. it's good. but not essential for me.

edit:> 
It almost certainly has at least some XUL component. Many Firefox extensions could probably be ported trivially to Konqueror, but I doubt there are any Firefox extensions that you could download and have just work in Konqueror (unless it were to actually be a standard Netscape plugin).

no what he said was that it was mostly XML and javascript and html, so that a script could be written to make it work in Konqueror, and that there was a site where people did this often and posted the scripts. he said kdeaddons.org, which doesnt exist. And i havent found anything like it at kde-apps.org

---

### Post by kerry_s on 2006-10-10
The only thing i can think of is just bookmark your google notebook site and use split panel.

---

### Post by maniacmusician on 2006-10-10
damn, you can do split panel?

that still doesn't give me super cool right click access, but it's definitely cool! how'd you do that?

---

### Post by fuscia on 2006-10-10
> **maniacmusician said:**
> damn, you can do split panel?

that still doesn't give me super cool right click access, but it's definitely cool! how'd you do that?

right click on the status bar.

---

### Post by kerry_s on 2006-10-10
LOL
Right click the panel at the bottom of konqueror or you can add the icons to the tool bar. I use the icons on the toolbar. You'll find the little tricks konqueror can do as you use it more.
 
If you want to get that close button hidden under the icon and be able to close tabs with middle mouse click.
goto> /home/(user)/.kde/share/config/konquerorrc <(user) is your name


add these lines under [FMSettings]

HoverCloseButton=true
MouseMiddleClickClosesTab=true
and change
PermanentCloseButton=true
to
PermanentCloseButton=false

---

### Post by maniacmusician on 2006-10-10
thats awesome! thank you.

---

### Post by kerry_s on 2006-10-10
I can tell, once you get familiar with that split screen, you'll be splitting screen all over the place. You can resize them you can have different splits on different tabs, you can keep splitting each indivdual window. I'll often be browsing several forums at one time. Have fun.

Check this site out-> [http://kudos.berlios.de/kf/kisimlar/tipsntrix.html](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html)

---

### Post by maniacmusician on 2006-10-10
i bet! it's a really cool function. wish i'd discovered it earlier. still missing google notebook, but i'll live. certainly better than having swiftfox crash just because i have 2 windows with 20 or so tabs open.

---

### Post by fuscia on 2006-10-10
the split screen is awesome for keeping track of my fantasy football disasters.

---

### Post by kerry_s on 2006-10-11
I'm not sure if you want this tip or not, but i'll post just in case. In kubuntu the konqueror is actually crippled to make it simpler. To uncripple run this in terminal->

cp /usr/share/apps/konqueror/konqueror-orig.rc ~/.kde/share/apps/konqueror/konqueror.rc

---

### Post by maniacmusician on 2006-10-11
what do you mean by crippled? when uncrippled, what will it hold as opposed to when crippled?

---

### Post by kerry_s on 2006-10-11
It's crippled in the menus, compare yous to mine.pic->

---

### Post by maniacmusician on 2006-10-11
oh wow. what crap. i'm definitely uncrippling it. And about something you posted before,

> If you want to get that close button hidden under the icon and be able to close tabs with middle mouse click.
goto> /home/(user)/.kde/share/config/konquerorrc <(user) is your name


add these lines under [FMSettings]

HoverCloseButton=true
MouseMiddleClickClosesTab=true
and change
PermanentCloseButton=true
to
PermanentCloseButton=false
Reply With Quote

dont really get what that means. could you explain a little so i know what I'm doing? I dont know which "close button" you're talking about.

---

### Post by kerry_s on 2006-10-11
Oh, sorry, you proably never activated it then.
settings> configure konqueror> web behavior> advanced options, you should see "show close button instead of website icon".

That tweak combines the website icon with the close button, so when you hover over the tab icon it shows the close button. The other ones just makes it able to close with middle click.Here a pic the left shows the icon, the right is my mouse hovering on it.->

---

### Post by Bloodfen Razormaw on 2006-10-11
Awesome tips.  I didn't know about the middle click option for closing.  Although I usually use mouse gestures to close tabs, I never use the middle click on a tab to load a URL, so I think I'll enable it.

Another useful tweak:  If you use Konqueror for a while you will find that its access keys can get annoying.  You only need to hit one key to turn them on, Ctrl.  Hit Ctrl and change your mind about your shortcut key and you will end up accidentally activating something.  It's better than the IE/Mozilla way (which actually lets access keys overwrite application shortcuts!), but annoying in its own right, and you will probably come across that sooner or later.  To disable them, add

```

[Access Keys]
Enabled=false
```
to your ~/.kde/share/config/konquerorrc file.

---

### Post by maniacmusician on 2006-10-11
thanks to everyone for contributing so far.

another question; i've heard that konqui already has a lot of features from ff extensions built in. How about a session manager? i usually have tons of tabs open and it's important that i have an easy way to get to them.

---

### Post by ComplexNumber on 2006-10-11
what do kde/konqueror users do when they have lots of bookmarks, and hence, a bookmarks menu that fills the whole screen?

---

### Post by Bloodfen Razormaw on 2006-10-11
> another question; i've heard that konqui already has a lot of features from ff extensions built in. How about a session manager? i usually have tons of tabs open and it's important that i have an easy way to get to them.
It doesn't save them on close, you have to do it manually.  This is one of the most asked for features.  Right now the Konqueror session system is made for orienting it towards different tasks, like web browsing and file browsing.  They really ought to ditch that since Konqueror's whole purpose is to merge all of that together ("ln webbrowsing filebrowsing" is your friend :P).  Konqueror should have the same session options as Kate does now.  I expect they will do this eventually, but not in the KDE 3 series.  KDE developers don't typically replace things until major versions changes to keep users of the present system happy, even if there are only three of them (Noatun users, I'm looking at you).

> what do kde/konqueror users do when they have lots of bookmarks, and hence, a bookmarks menu that fills the whole screen?
Organize them :P

---

### Post by maniacmusician on 2006-10-11
how do i save them manually? i have to bookmark them all? that wouldn't be too bad i suppose. 

I cant wait for kde4. fun stuff.

edit: as long as I have this thread, might as well ask some more stuff.

if any of you use gmail, how do get it to display correctly? I mean in standard view with the chat on. If I change browser id to mozilla 1.7.3, and open an email, i get "Arrgh! the page has been corrupted!" and the chat doesnt display correctly. If i set it to IE it tells me i have to turn on ActiveX controls or something. so how do you guys do it?

Also, in firefox, when I click the middle mouse button on a web page, I get the little circle with the arrows that allows me to scroll really fast through web pages. Can i enable this in konqueror? (i havnt really tried yet; but all the options seem pretty confusing)

---

### Post by Bloodfen Razormaw on 2006-10-11
Go to Settings->Save View Profile.  Make sure the Save URLs to Profile box is checked and click Save.

There is also a Konqueror extension in kdeaddons I believe that can recover URLs after a crash, and Konqueror automatically restores sessions if it is running when you log out.  But I don't think there is a way to have to automatically restore a session after quitting it normally.

---

### Post by maniacmusician on 2006-10-11
cool, thanks. But i usually have my tabs in 2 windows...20 tabs is too much for one window. In that case, I think i'll just use "Bookmark tabs as folder".

also, please see my edit above (more questions :p)

---

### Post by Bloodfen Razormaw on 2006-10-11
Re: Gmail
I don't use it myself, but as I understand it there is a specific workaround in Konqueror for Gmail, to make it support the Safari version of Gmail.  It should work if you set your user agent to Safari.

Re: Middle clicking
It works for me.  You might need to disable the middle click opens URL in selection option if it is on (I don't remember if it is by default).  It is under the Konqueror Settings in Web Behavior, in the Mouse Behavior box.  You might also want to try out the nice auto-scroll feature.  Shift+Up or Down makes it automatically scroll in that direction.  Doing it again speeds it up.  Hitting Shift again makes it stop.

---

### Post by maniacmusician on 2006-10-11
no, safari as a user agent doesnt work...

when I middle click, it does a "locate" thing instead of turning into a scroller, so its not exactly opening a url. 

the keyboard scrolling is pretty good; if i'm using a keyboard. i'd like to have a mouse option too.

---

### Post by kerry_s on 2006-10-11
Have you tried to set it to firefox? I've got mine set to firefox 1.5.0.4 for google.com.

Yeah, i didn't even know there was a auto scroll for the mouse till i turned off that middle click opens url.

---

### Post by maniacmusician on 2006-10-11
I dont have that as an option...i think mine is still "crippled". I tried copying the file that you pointed out on the previous page, but that hasnt uncrippled it. I still dont have all those options that you have.

---

### Post by kerry_s on 2006-10-12
Did you try logging out and back in?

---

### Post by maniacmusician on 2006-10-12
no didnt even think of that. so logging   out and in    gave me all those options, but i still dont have firefox 1.5 as one. The closest i have is firefox 1.0 . I also have mozilla 1.7.3, and thats decent i guess, but it doesnt compare, see screenshots. konqueror doesnt look as nice and it doesnt bring up the chat thing correctly. I guess i'm just quibbling now, but the looks seem like a css thing, if you look at the body of the message. The backgrounds are different, ff shows the rounded corners and konqueror doesnt.

and firefox 1.5 still doesnt show up as an option for me..

---

### Post by kerry_s on 2006-10-12
Have you updated to the latest 3.5.5? That's what i've been using.pic->

---

### Post by maniacmusician on 2006-10-12
no...do you really think that will make a difference? kind of seems like a hassle to do it. 

i'm on 3.5.3.  if you really think it will help....how did you go about doing it? does it involve compiling crap and stuff?

---

### Post by kerry_s on 2006-10-12
I'm really not sure it would help, i'm sure i've always seen the firefox option, so it's strange you don't have it. The upgrade is easy you just add the repos and update, since your using 3.5.3 i'm guessing your using dapper(i'm on edgy). Just follow the instructions on the kubuntu site-> [http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php)

Sorry i can't be of more help.

---

### Post by greggh on 2006-10-12
> **kerry_s said:**
> I'm really not sure it would help, i'm sure i've always seen the firefox option, so it's strange you don't have it. The upgrade is easy you just add the repos and update, since your using 3.5.3 i'm guessing your using dapper(i'm on edgy). Just follow the instructions on the kubuntu site-> [http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php)

Sorry i can't be of more help.

Does that give you a customized Kubuntu 3.5.5 desktop or a default generic KDE 3.5.5 desktop?

---

### Post by kerry_s on 2006-10-12
It depends on what you install. The repo just provides packages. For instance i only use kde-core on a server install, so i don't get no kubuntu branding and stuff. If you just grab kde it will be regular kde.

---

### Post by greggh on 2006-10-12
> **kerry_s said:**
> It depends on what you install. The repo just provides packages. For instance i only use kde-core on a server install, so i don't get no kubuntu branding and stuff. If you just grab kde it will be regular kde.

Hmmm. Still confused. Let's say you have a Kubuntu branded desktop already and then go to install those new 3.5.5 packages, will your Kubuntu desktop then turn into a plain KDE desktop?

---

### Post by kerry_s on 2006-10-12
Nope, your running kubuntu already so it updates the kubuntu stuff as well.

---

### Post by greggh on 2006-10-12
> **kerry_s said:**
> Nope, your running kubuntu already so it updates the kubuntu stuff as well.

Thanks for the info. Much appreciated.

---

### Post by maniacmusician on 2006-10-12
> **kerry_s said:**
> The only thing i can think of is just bookmark your google notebook site and use split panel.
firstly, how did you get the notebook to display correctly? mine doesn't load. and secondly, How can I make the split screen exist for all tabs at the same time? or is that not possible? 

thanks

---

### Post by kerry_s on 2006-10-12
"how did you get the notebook to display correctly?"

I have konqueror to identify as firefox. According to the kde site that's the only way to get konqueror to work with gmail.


"How can I make the split screen exist for all tabs at the same time? or is that not possible?"

I don't no, i've always just split it again on other tabs, that's why i prefer the icons instead of right clicking the bottom bar.

Sorry i can't help more, i'll look around and let you know if i come across anything that can do that.

---

### Post by Bloodfen Razormaw on 2006-10-12
> firstly, how did you get the notebook to display correctly? mine doesn't load. and secondly, How can I make the split screen exist for all tabs at the same time? or is that not possible? 
You can't make it so a new tab automatically splits itself.  There may be some way around that using the hot keys functionality, to assign a keyboard shortcut or mouse gesture to make execute a kfmclient command that opens one, uses a dcop call, or just combines several other keyboard shortcuts to do it, so long as you open the new tab with that method.

---

### Post by maniacmusician on 2006-10-12
okay, thanks. the thing that's really frustrating me is that gmail doesnt open correctly (pages often show up as "corrupted"). it sucks to have to open up a mozilla based browser just to check my email. Does anyone know why I don't have firefox 1.5.04 as an option?

also, the "browse" view at the pirate bay ([http://thepiratebay.org](http://thepiratebay.org) ) doesnt display correctly for me. when it lists the torrents they come out as plain text. then i change the browser id, and it works. until i move to another page, then it stops working again. so i have to constantly change my browser id at every page for it to work, which is a hassle. Not a huge deal though, as I dont use the site too often.

i just want ma gmail.

---

### Post by kerry_s on 2006-10-12
You can set it so the id covers the whole site, using the site specific identification, that way you don't have to keep changing it for each page.

Did you look at updating to the lateast kde release at that link i posted?

---

### Post by maniacmusician on 2006-10-12
I did set it to cover the whole site. It just for some reason stops working after I move to a different page. and if i reset it (doesnt usually matter which browser i reset it to) it'll show again, for the duration of the time that i'm on that page.

i looked at it but havnt updated yet...can i go straight from 3.5.3 to .5, or do i have to go to .4 first?

---

### Post by Bloodfen Razormaw on 2006-10-12
> okay, thanks. the thing that's really frustrating me is that gmail doesnt open correctly (pages often show up as "corrupted"). it sucks to have to open up a mozilla based browser just to check my email. Does anyone know why I don't have firefox 1.5.04 as an option?
If you add Firefox to your KMenu you will have an option for it when you go to your file associations, and you can add it as an option to open HTML.  You can add Firefox to your Kmenu automatically with the menu updater tool.  While you are at it, send Google a mail asking that they start using standard Javascript for Gmail instead of IE/Mozilla specific extensions.  Kind of a shame they dropped Kecko.  The KDE developers actually managed to do in four days what GNOME has failed to do for a half decade: ported Gecko to their native toolkit.  They had an experimental Gecko KPart you could embed in Konqueror, and switch between it and KHTML with the View Mode option on the fly.  Used KDE natively for drawing the page, no XUL BS.  As I recall they dropped it because Mozilla refused to support a version of Gecko that wasn't crippled with XUL.

> also, the "browse" view at the pirate bay ([http://thepiratebay.org](http://thepiratebay.org) ) doesnt display correctly for me. when it lists the torrents they come out as plain text. then i change the browser id, and it works.
I can't reproduce that.  It looks fine to me.

---

### Post by darkhatter on 2006-10-12
I just set it to Safari, or firefox and most sites work for me (mainily gmail)

---

### Post by maniacmusician on 2006-10-12
> **Bloodfen Razormaw said:**
> If you add Firefox to your KMenu you will have an option for it when you go to your file associations, and you can add it as an option to open HTML.  You can add Firefox to your Kmenu automatically with the menu updater tool.  While you are at it, send Google a mail asking that they start using standard Javascript for Gmail instead of IE/Mozilla specific extensions.  Kind of a shame they dropped Kecko.  The KDE developers actually managed to do in four days what GNOME has failed to do for a half decade: ported Gecko to their native toolkit.  They had an experimental Gecko KPart you could embed in Konqueror, and switch between it and KHTML with the View Mode option on the fly.  Used KDE natively for drawing the page, no XUL BS.  As I recall they dropped it because Mozilla refused to support a version of Gecko that wasn't crippled with XUL.


Why do they need mozilla to support it? couldnt they just have used it under the terms and conditions mozilla's mpl license? That would the most amazing feature for Konqueror to have.
> **Bloodfen Razormaw said:**
> 
I can't reproduce that.  It looks fine to me.
I think it's because I don't have the Firefox 1.5.04 option for user agent switching. I'm pretty sure that I have firefox in my Kmenu, always have. I'm posting screenies of what pirate bay looks like when screwed up. first one is the screwed up one. So i just change the browser in user agent switching (yes its applied to the whole site), and it refreshes fixed. (2nd screen).

---

### Post by Bloodfen Razormaw on 2006-10-12
> Why do they need mozilla to support it? couldnt they just have used it under the terms and conditions mozilla's mpl license? That would the most amazing feature for Konqueror to have.
Maintaining their own Mozilla tree would have been a huge amount of work.  Mozilla's code is not exactly the highest quality out there.  Maintaining it would detract a lot of resources from other more important projects.

> I think it's because I don't have the Firefox 1.5.04 option for user agent switching.
Ah, you mean the user agent menu.  Still, I don't switch user agents on that site and everything looks like it does in your second pic.

Edit: Why don't you paste your exact user agent string.  You can see what is being used in the user agent options.

---

### Post by maniacmusician on 2006-10-12
...my user agent string? I'm going to take a stab at this, dunno if its what you want.

right now it's on Mozilla 1.7.3 on windowx xp...i think this is the user agent string: Mozilla/5.0 (Windows; U; Windows NT 5.1; en_US; rv:1.7.3) Gecko/20040916

---

### Post by Bloodfen Razormaw on 2006-10-12
Using that user agent string I can still load the page without trouble.  Is that the one you are using to fix it, or the one that gives you problems?

---

### Post by maniacmusician on 2006-10-12
they ALL give me problems. it doesnt matter which one i use. At first attempt, the site will not load properly. Then, I change the user string. It doesnt matter what i change it to, it can be anything, and the site works. 

BUT

if I navigate away from the page that I am on, it once again gets screwed up. So pretty much, if i want to view the pages correctly, I have to change the user agent setting every time i click a link.

---

### Post by kerry_s on 2006-10-12
It sounds like your kde settings is not right. I think you should try renaming the .kde folder to .kde.old then log out and back in, it should make a new kde folder with all the original settings. If it's okay you can then delete the old one, if it's the same just delete the new one and rename the old one back.

---

### Post by maniacmusician on 2006-10-12
before I take the plunge and do this, what other applications and settings will this affect? i'm pretty sure i've tweaked stuff in the past

---

### Post by Bloodfen Razormaw on 2006-10-12
It will affect all your KDE applications by returning them to their default values (and restoring your old .kde directory will change everything back).  In all honesty I doubt it will matter.  This doesn't sound like a configuration problem to me.  Since you are having this bug and others aren't, I'm guessing it might be because you are using Kubuntu and I and some others here are using regular KDE.  A lot of patches Kubuntu applies to KDE are of dubious quality.

---

### Post by maniacmusician on 2006-10-12
is there really any difference between kubuntu and kde?

---

### Post by Bloodfen Razormaw on 2006-10-12
Kubuntu-desktop uses a heavily modified version of KDE.  A lot of the changes they made are rather...bad.  The crippling of Konqueror was mentioned already.  Another example is the way that they moved the tabs in Konsole from the bottom to the top, in defiance of the decision the KDE developers made for maximum usability.  When using a terminal you spend most of your time looking at the bottom of the display.  And a lot of Kubuntu packages are very unstable while they work fine in other distributions.

---

### Post by maniacmusician on 2006-10-12
my konsole tabs are still at the bottom...

But i don't understand. what's the point in making all these crippling changes? why would anyone even use kubuntu then? are there any positive changes?

the System Settings redo of Kcontrol is kubuntu-specific right? i happen to like that one. but i havnt noticed much else.

---

### Post by Bloodfen Razormaw on 2006-10-12
They must have changed back Konsole then.  The KDE developers were complaining to them quite loudly about it.

The problem is that Kubuntu is making the same mistakes GNOME does--mistaking simplicity with usability.  The lack of a necessary feature is crippling to users, while the presence of unused feature is easily ignored.  Hence they use a stripped down Konqueror.  Apparently they decided all on their own that KDE's excellent showings in usability studies is a series of unlikely flukes.  Konqueror has a Simple Browsing profile that provides a simple interface, but for some inexplicable reason they felt the need to instead modify the XMLGUI file to take the features out every which way.  I can't even imagine the rationale behind that.

Personally I would say there is little to no reason to use Kubuntu over standard KDE.

---

### Post by kerry_s on 2006-10-13
Hmm, I didn't think that they might have crippled it that much.

Do you think if he tried reinstalling kde-core it would bring the kde settings back?

I'm running edgy-server-install + kde-core to keep my system small and fast. I don't see any kubuntu stuff other than the konqueror introduction menu where it has "about kubuntu".

I thought just running these lines in konsole was suppose to uncripple konqueror.->

cp /usr/share/apps/konqueror/konqueror-orig.rc ~/.kde/share/apps/konqueror/konqueror.rc

cp /usr/share/apps/konqueror/profiles/* ~/.kde/share/apps/konqueror/profiles/

---

### Post by kerry_s on 2006-10-13
Okay here is what i found on the kubutu site-> [http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)

How do I change Konqueror back to the default KDE profiles?
Kubuntu Breezy and Dapper come with a simplified Konqueror profile to make things more use friendly compared to default KDE.
To get back to the default KDE profiles:
sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc

To enable Konqueror to open tar and zip files:
rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/

---

### Post by kerry_s on 2006-10-13
On my install i don't have /usr/share/kubuntu-default-settings
so i'm guessing only konqueror was crippled.

---

### Post by maniacmusician on 2006-10-13
thanks for the info. for edgy, I'm going to do a fresh installation. But the problem is, I can't do it the way you did (server installation + kde-whatever [i dont want core]), because my wireless card isn't supported out of the box. I have to first install ndiswrapper and set up all that stuff, which can be painful if i have only the command line. 

i appreciate the fact that the server installation is a lot lighter, but at the same time, i dont want to be stuck with too little features. feels like you never know what you have until it's missing.

---

### Post by Bloodfen Razormaw on 2006-10-13
If you are going to install from the ground up, you might want to try Debian.  Nicer packages (especially KDE packages), and you can get a full CD/DVD set with the entire repository, so you will have everything whether or not you are connected immediately.  And Debian installed with just base is very slim.  Add on the basic software task to get all the non-essential stuff you expect to have.  After that maintaining an Ubuntu and Debian system is pretty much identical.

---

### Post by maniacmusician on 2006-10-14
i've sneaked a look at debian before, but to be honest, i like ubuntu based things a little better

---

