---
title: "Unity8 back in buisness?"
date: 2016-05-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-05-04
Looks like Uniy8+xmir are back in buisness. I'll try and get the links up. Also a program called libertine will run traditional  apps on Unity8 . I am experimenting now.

regards..

---

### Post by dino99 on 2016-05-04
yes devs are very busy developing/fixing it; but will not be default again.
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.10-No-Unity-8-Default](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.10-No-Unity-8-Default)

---

### Post by ventrical on 2016-05-04
dino,

I have unity8 working with Libertine to install traditonal debs .. but need exact link to deb . Can you give me some examples .. ie; like firefox for instance/

thanks

regards..

---

### Post by dino99 on 2016-05-04
Sorry, but you might be the most experienced tester about that project; myself i have never tried installing/testing it (only following the news on my side for the time being)

---

### Post by ventrical on 2016-05-04
It appears libertine is not entirely functional atm for amd64 desktop applications but in theory I can see where they are going. All the groundwork is being done.

regards..

---

### Post by ventrical on 2016-05-04
Browser is worse than ever :)

---

### Post by grahammechanical on 2016-05-04
I wish I could join this effort but on my system unity8 session is still no-go for lift off on Nvidia - Nouveau. The switch over to Mir does not complete. Black screen. It has been like this for months.

From the UOS sessions it seems that unity8 session has gone from being a pre-view to being the intended Xserver Ubuntu replacement. 

Regards.

---

### Post by ventrical on 2016-05-04
> **grahammechanical said:**
> I wish I could join this effort but on my system unity8 session is still no-go for lift off on Nvidia - Nouveau. The switch over to Mir does not complete. Black screen. It has been like this for months.

From the UOS sessions it seems that unity8 session has gone from being a pre-view to being the intended Xserver Ubuntu replacement. 

Regards.

Correct .. and no snappy personal in sight.

Regards..


ps .. If I do full reboot it loads. If I do log off and log on it will not work. Will try on nVida machine.

---

### Post by ventrical on 2016-05-04
Did you use:

```

sudo apt-get install unity8-desktop-session-mir

```

---

### Post by ventrical on 2016-05-04
It is working here on nVida .. but browser don't work just yet..

---

### Post by grahammechanical on 2016-05-04
> It is working here on nVida

That is discouraging from my point of view. Fresh install of Yakkety from a daily image. Correct install command lifted from the wiki page. Lots of packages installed and a restart. Change session and log in. Not even the hardware cursor appearing.

---

### Post by mc4man on 2016-05-04
Well I can get the browser working in 8 & also open the store though nothing can actually be installed, (it trys & fails...
So reasonably & continuing useless, too bad the unity browser doesn't seem able to browse a file system.

---

### Post by ventrical on 2016-05-05
Mark Shuttleworth is adamant that he will have unity8 as the default desktop for 16.10. He also used the term 'overpromise' when mentioning that he did not want to 'overpromise' certain things in certain areas of development but I think the unity desktop team got the message about unity8. This being the case, there could be rapid development forthcoming. eh .. me always have high hopes :)

regards..

---

### Post by mc4man on 2016-05-05
> **ventrical said:**
> It is working here on nVida .. but browser don't work just yet..
Try installing - cgmanager libpam-cgfs

---

### Post by ventrical on 2016-05-05
I have a problem on one yakkety install... When I log on I notice I am getting a run on my modem meaning that there is an update  going on. This happening since unity8 install. Could this be an OTA update?

Also 

```

Reading state information... Done
cgmanager is already the newest version (0.41-2).
libpam-cgfs is already the newest version (2.0.0-3).
libpam-cgfs set to manually installed.

```

---

### Post by grahammechanical on 2016-05-05
> Could this be an OTA update?

Ubuntu desktop does not use the same update channels/repositories as Ubuntu phones/tablets. Or so I believe. The switch from X Server to Mir may break connection to the modem. 

Regards

---

### Post by ventrical on 2016-05-05
Actaully it 'runs' the network when I log on to mir/unity8. it is about a 3 minute run. have no idea what is going on.

regards..

---

### Post by ventrical on 2016-05-05
> **mc4man said:**
> Try installing - cgmanager libpam-cgfs

It works just fine with Intel. The nVidia install will not work with mir I guess. I hope they fix it so grahammechanical can get back testing.

Improvement: I can use my mouse wheel.
Problem: Only seems to work on xenial atm
Experiment: Perhaps Libertine will now work.

regards..

---

### Post by ventrical on 2016-05-05
YouTube with awesome audio and video def!

regards..

---

### Post by grahammechanical on 2016-05-06
> I hope they fix it so grahammechanical can get back testing.

They want the Unity 8 log in option to be part of the Yakkety ISO image for 16.10. And Unity 8 will need to load on all video hardware because when non-testers start seeing that option they will not be thinking, "it is only a technology pre-view." Unity 8 will also need to offer something like the usefulness of Unity 7 even if it does it differently and incompletely.

QA will need test cases for Unity 8. A lot of ISO testing at the end of summer.

Regards.

---

### Post by ventrical on 2016-05-07
> **grahammechanical said:**
>  Unity 8 will also need to offer something like the usefulness of Unity 7 even if it does it differently and incompletely.


I can see more and more how difficult this will be. It would require current unity8 desktop developers to either back step or work diligently on xmir and other components to parse out older graphical hardware and roll it upwise  to another available  and compatible desktop environment. It will have to be better that llvmpipe. What  has happened in the past several cycles is sort of like going to an optometrists office. There are younge doctors and more senior doctors. The younger doctors use newer equipment. They have lens selectors on a carrouselle and it is easy for them to roll to different lens specifications. They are all on the same rack. The elder more traditional approach is to use a slower method. The lenses have to be inserted manually. This is what llvmpipe is doing. There is no reason why lenses (or scopes) cannot fit into the same carrouselle despite the age of the graphical adapters up to a point. It may mean implementing a new video server that is lean on resources. Another example is  a  mechanical slide projector. It is a simple machine yet it can display low definition  still graphics and high definition still graphics all through the same scope . Why does it have to be so complex. 

> 
QA will need test cases for Unity 8. A lot of ISO testing at the end of summer.

Regards.

Something to look forward to for testers. :)

Regards...

---

### Post by grahammechanical on 2016-05-07
At UOS Will Cook demonstrated ISO testing but he could not use Ubuntu Yakkety to show where the test cases are because there are no test cases for it on iso.qa. The original test cases apply to the Ubuntu ISO of today but not to the Ubuntu ISO that people will be using to install 16.10.

From that UOS summit it seems that Canonical engineers have realised that if they do not start snapping applications like Firefox & Libreoffice the change over to Unity 8 default will take much, much longer.

Worried about someone reading your emails? Send confidential information by fax. Old technology but much more secure than emails.

Regards

---

### Post by ventrical on 2016-05-07
I had seen Firefox and LibreOffice running on Unity8 through a libertine container but *THAT* one  demo (and there was only one) was done on a specialty device and most likely on a virtual machine. Bottom line , and I say this with a sensitivity in mind, libertine containers are useless on an amd64 desktop form factor. For the most part it is wishful thinking and I do not have a problem with that.  You can fool some of the people some of the time ...

 Libertine is very enthusuastic. It is the solution to the problem and it may take time to build the bridge for amd64 desktop form factors. Snappy_personal is also very adventurous but it has big problems.

  In my correspondence with Will Cooke and Mark  they just fell short of committing that there would be a new snappy personal image in May and that  they couldn't wait to get their hands on a spin.  This  was a bright spark as I would say. But Will also put a little bit of a damper on it by talking about the complexities.. etc..   Mark's further discussion in his plenary discusses the term 'overpromise' and so  Mark  is basically saying that  he does not want to put pressure on the unity8 team and take something out of the oven until it is fully cooked and can be used safely by everyone in the community. Despite my personal views , I think this  is a well seasoned and tempered approach to follow. It is the wise thing to do and I for one am not going to question Mark's experience in making such a decision.

  Seeing how diverse and flexible the ubuntu community is, I think some  interesting biscuits and tools will come down the pipe for early adopters to cut their teeth on. :)

Stay tuned :)

Regards..

---

### Post by mc4man on 2016-05-07
Though many times in the past I think some Ubuntu 'overpromise''s where more a tactic then a miscalculation.'

---

### Post by ventrical on 2016-05-07
It's a joy to conceptualize about these things but one can feel the weight when looking to assemble all the cogs, wheels and bases. Yes .. it can wipe the smile right off of our faces ...;)

Regards..

---

### Post by grahammechanical on 2016-05-07
> In my correspondence with Will Cooke and Mark

At least you let them know that there are people around like us who are interested enough to test early versions and see how it grows.

---

### Post by ventrical on 2016-05-08
> **grahammechanical said:**
> At least you let them know that there are people around like us who are interested enough to test early versions and see how it grows.

I have been very persistent and they have been very responsive. Although I must sat that Mark did say something about a working unity8 and how he wants to keep it in house (with developers) but I'm still working on them.. and so I am going to keep my yakkety proposed repos open.

---

### Post by grahammechanical on 2016-05-08
Could it be that developers use a special branch of the code (on Git) when they test their work? Perhaps we need to learn how to install extra special branches of the code. The proposed repo is too tame. We want a wild Yak not a domesticated animal.

EDIT: It is on bzr.

[https://unity.ubuntu.com/getinvolved/development/unity8/](https://unity.ubuntu.com/getinvolved/development/unity8/)

[https://code.launchpad.net/unity8](https://code.launchpad.net/unity8)

I might be tempted to try this later

Regards

---

### Post by ventrical on 2016-05-08
> **grahammechanical said:**
> The proposed repo is too tame. We want a wild Yak not a domesticated animal.


:) That's worth a Nobel Prize in literature..


ahh .. boy oh boy .. thats just too precious :)ROTFLMAO!

Regards..

---

### Post by ventrical on 2016-05-08
> **grahammechanical said:**
> Could it be that developers use a special branch of the code (on Git) when they test their work? Perhaps we need to learn how to install extra special branches of the code. 

EDIT: It is on bzr.

[https://unity.ubuntu.com/getinvolved/development/unity8/](https://unity.ubuntu.com/getinvolved/development/unity8/)


I might be tempted to try this later

Regards

 This might be the undertaking. It says for 15.04  (vivid) so are you saying we should experiment with these steps on yakkety?

Regards..

---

### Post by grahammechanical on 2016-05-08
It also mentions xenial. No PPA needed for xenial. I have tried this on Yakkety. From the viewpoint of an ignorant experimental tester, I would say the instructions are incomplete. Something called cmake was not installed. And there were other errors.

I did get a kind of unity 8 loading. A small window about phone size but something was incomplete. The scopes were there but it was as if the icons for them had not been coloured in. It certainly was not an up to date unity 8 as we have seen in the demos. I also had unity8-desktop-session-mir installed. I am not sure if that helped.

I have put in a clean install of Yakkety & I will try again and this time I will install ubuntu-dev-tools & cmake in advance. There certainly should be a code branch which the devs run to test their patches. That link was the best that I could come up with for now.

Regards

---

### Post by ventrical on 2016-05-08
I reviewed Mark's plenary and paraphrased some of his dialog:

> 

Mark Shuttleworth comments on unity8 (paraphrase) during Plenary session.



Question: Whats the priority of the new unity8?

Mark: "You will be able to get 16.10 with Unity8 just like you can get 16.04 with Mate or Gnome, Right? .. It will be there .. it will be an option and the team that is working with that is commited to make that a first class option. You ask .. you know .. whats the priority.. for about 80 people .. that is their top priority..that is what their forcused on...they are working on juggling all the pieces.. to get that into a fit state..ahmmm...for the people working on cloud it is not a priority at all.. and we kind of have to be that way .. we have to seperate our areas of interest so we can have teams just worry about doing one things really , really well. The unity8 and the desktop team .. thats their top priority.! We know we have a big community that will lead KDE that will lead Gnome...ummm I'm super confident in their work.. we are focused on unity8 and the unity8 community is focused on unity8.. and that's their top priority..umm I want to be running unity 8 as my desktop for 16.10. I'm pretty sure that that's going to be a pretty brittle and ropey experience..uh .. it's going to be a 1.0 brand new desktop environment..brand new story.. ahhm..I'm also pretty sure it will <clean up really quickly>? What the exact timelines on that are ? Difficult to tell. I have said publicly I'd like the community to tells us that unity8 is ready to be  the default  ubuntu experience. I think I made a mistake because I was so convinced in the convergence story, moving unity7 into position before it was .. before it was ready. uhm..in 11.04 So..lessons learned and I think the right way to deal with that is to make a great unity8 desktop **use it ourselves** and then let people vote essentially and signal that this is what they want as the default ubuntu.



I am not exactly sure what Mark meant by "Use it ourselves". I assume he is talking about unity8 and the unity8 team exclusively in which he is the team captain. If this is the case (and I am not entirely sure) it means, basically that we will be getting  very small bones thrown at us ;) to chomp on. 

 As I read between the lines in Mark's comments he is not entirely sure of the current progress. This tells me that there are problems with the unity-compositor, xmir and binding the desktop to the kernel in a workable and reliable fashion. Just from my experience in experimenting with past versions I can tell that they are trying to build and patch bind emulators between xmir and unity8 and it is failing for the amd64 desktop experience. This was where libertine was suppossed to come in. So could the problem be with libertine? 

 There is another problem also. If they try to inject older code to work with xmir , lets says for instance a xserver emulator (that would resemble a facsimile of llvmpipe on older versions of unity starting since 12.04 version) then xmir will not be a top-down, bottom-up newly written program. There will be old code in there and they would not be able to call it their own.   

  I would just suggest that we keep working on it behind the scenes. Try some of the current steps .. experiment and see if there is somthing missing. Try to break it .. ya know. If they don't let us in to try and break it in the wild then there will be major bugs down the road.

  I looked at the some of the source code and most of it is just calling modules and objects. It would take me a bit to refresh myself in this style of programming. I am not going to attempt to rewrite it but we can test in  other ways and just keep filing bugs.

Thanks for links and suggestions. I have two yakkety installs with unity8 both with libertine.  I do have the very new improved browser working well on one install and you can log in with your username and password. I am going to keep hammering on it. :)

regards..

---

### Post by grahammechanical on 2016-05-09
As Unity 8 is to be a log in option for 16.10 then it would not be sensible to develop Unity 8 on 16.04 because a lot of work will need to be done transitioning to Yakkety code. I understood Mark's comments about using it ourselves to mean that Canonical will not force Unity 8 as the default session until they are confident that users are happy with it and expect it to be the default option.

Remember the surprise everybody got when they installed or upgraded to 11.04? I was not surprised because I was running the development version. I knew what was coming. Mark says that they have learnt lessons from the mistake in making Unity the default UI before it was ready & people wanted it.

I think Mark was talking to us. Who is the Ubuntu Community? The millions who use Ubuntu? Or, the thousands who contribute in large or small ways and are interested in the future development of Ubuntu?

Just as 16.10 will have Unity 7 as default with Unity 8 as an option, so it could be that 17.04 or 17.10 will have Unity 8 as the default with Unity 7 as an option. And then by 18.04 LTS the default may well be Unity 8. A lot of people will need to be running Unity 8 as a daily driver and giving feed back if Unity 8 is to become default.

Regards.

---

### Post by ventrical on 2016-05-09
> **grahammechanical said:**
> As Unity 8 is to be a log in option for 16.10 then it would not be sensible to develop Unity 8 on 16.04 because a lot of work will need to be done transitioning to Yakkety code. I understood Mark's comments about using it ourselves to mean that Canonical will not force Unity 8 as the default session until they are confident that users are happy with it and expect it to be the default option.

Remember the surprise everybody got when they installed or upgraded to 11.04? I was not surprised because I was running the development version. I knew what was coming. Mark says that they have learnt lessons from the mistake in making Unity the default UI before it was ready & people wanted it.

I think Mark was talking to us. Who is the Ubuntu Community? The millions who use Ubuntu? Or, the thousands who contribute in large or small ways and are interested in the future development of Ubuntu?

Just as 16.10 will have Unity 7 as default with Unity 8 as an option, so it could be that 17.04 or 17.10 will have Unity 8 as the default with Unity 7 as an option. And then by 18.04 LTS the default may well be Unity 8. A lot of people will need to be running Unity 8 as a daily driver and giving feed back if Unity 8 is to become default.

Regards.

I think your remarks represent a more positive analogy of the facts.

  I had a very good experience with Natty Narwahl but there was a lot of breakage for sure.

Regards..

---

### Post by PaulW2U on 2016-05-09
> **grahammechanical said:**
> Mark says that they have learnt lessons from the mistake in making Unity the default UI before it was ready & people wanted it.
Ubuntu 11.04 was a disaster, 11.10 was better but I don't think Unity was really ready until 12.04.
> **ventrical said:**
> I had a very good experience with Natty Narwahl but there was a lot of breakage for sure.
I didn't. I switched to Kubuntu for four years and only came back to Ubuntu when Plasma 5 became Kubuntu's default.

I don't mind running a development version, reporting bugs and testing ISOs but I expect something that is usable when the development cycle ends. I'm fortunate enough to have several items of hardware on which to run different Ubuntu versions and/or flavours. I await a finished Unity 8 with interest but it won't get any further than my test laptop until I'm really sure that it's **ready** for general release.

---

### Post by grahammechanical on 2016-05-10
I am not the only one having problems with unity8-desktop-session-mir but at least Michael Hall knows what he is doing. Which is more than I can say. I will try and follow this on a new install of Yakkety or even Xenial.

[http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

Regards.

---

### Post by ventrical on 2016-05-10
I checked it out. I am going to try on both yakkety and xenial. I am sending this message from ubuntu-browser using unity8 on yakkety. I cannot download the click files so I probably have to install the ppa.. but everything esle works except libertine .. so that will follow Mhalls steps.

regards..

---

### Post by QDR06VV9 on 2016-05-10
> **grahammechanical said:**
> I am not the only one having problems with unity8-desktop-session-mir but at least Michael Hall knows what he is doing. Which is more than I can say. I will try and follow this on a new install of Yakkety or even Xenial.

[http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

Regards.
Thanks graham for the link.

> **ventrical said:**
> I checked it out. I am going to try on both yakkety and xenial. I am sending this message from ubuntu-browser using unity8 on yakkety. I cannot download the click files so I probably have to install the ppa.. but everything esle works except libertine .. so that will follow Mhalls steps.

regards..
Are you guys having more success with intel vs nVidia systems?

---

### Post by ventrical on 2016-05-10
I cant get it to work so far.

```

ventrical@ventrical-MS-7850:~$ sudo click install --user ventrical com.ubuntu.terminal_0.7.170_multi.click
Cannot install com.ubuntu.terminal_0.7.170_multi.click: Signature verification error: debsig: could not open com.ubuntu.terminal_0.7.170_multi.click: No such file or directory

ventrical@ventrical-MS-7850:~$ 

```


Also the 

```

citrain host-upgrade 031

```

comes up with an error.
will try reboot.

---

### Post by ventrical on 2016-05-10
Is he working this through a VM?

---

### Post by QDR06VV9 on 2016-05-10
Hey vent from his google hang out [https://plus.google.com/+MichaelHall119](https://plus.google.com/+MichaelHall119)
> I_** took this screenshot from inside a native Unity 8 session, no VM, no LXC, just unity8-desktop-session-mir. **_I uploaded it to G+ from the Ubuntu Browser, from the File Manager, via Content Hub. The terminal is ssh'd into my home server where irssi keeps me on IRC 24/7. Dekko isn't shown, but it works fine too.  All I'm missing now is a good text editor.&#65279;

---

### Post by grahammechanical on 2016-05-10
"Disappointment haunted all my dreams." and it was not followed by "and then I saw her face" unity8. 

The PPA ci-train-ppa-service did not produce any 404 not found errors when installed in Yakkety. But the instructions fail to inform that we need citrain installed and citrain host-upgrade 031 needs to be run with sudo. An example of how developers are not seeing things from the point of view of an ordinary user with a default install of Ubuntu.

```
sudo apt install phablet-tools-citrain
sudo citrain host-upgrade 031
```

And it still loads to a black screen on Nvidia-Nouveau. A lot of work will have to be done otherwise there will be a lot of complaints from ordinary users come the autumn. Or should I say "the fall?" 

Regards.

---

### Post by ventrical on 2016-05-10
> **runrickus said:**
> Hey vent from his google hang out [https://plus.google.com/+MichaelHall119](https://plus.google.com/+MichaelHall119)

Thanks runrickus. Seen that link Was of no help.  Still .. that major unanswered question ; What hardware is he using ?  I would have  though that the lead in to his preamble would at least include hardware specs.

---

### Post by ventrical on 2016-05-10
> **grahammechanical said:**
> "Disappointment haunted all my dreams." and it was not followed by "and then I saw her face" unity8. 

The PPA ci-train-ppa-service did not produce any 404 not found errors when installed in Yakkety. But the instructions fail to inform that we need citrain installed and citrain host-upgrade 031 needs to be run with sudo. An example of how developers are not seeing things from the point of view of an ordinary user with a default install of Ubuntu.

```
sudo apt install phablet-tools-citrain
sudo citrain host-upgrade 031
```

And it still loads to a black screen on Nvidia-Nouveau. A lot of work will have to be done otherwise there will be a lot of complaints from ordinary users come the autumn. Or should I say "the fall?" 

Regards.

If it is any consolation .. same here.. however .. I did have some success with nVidia using yakkety and just installing unity8 from the universe repos. I got the browser to work .. but the other tools .. like the libertine/scope did not work . Workaraounds needed. .. no way . I'll just keep trying different things.

---

### Post by ventrical on 2016-05-10
> **grahammechanical said:**
> "Disappointment haunted all my dreams." and it was not followed by "and then I saw her face" unity8. 

The PPA ci-train-ppa-service did not produce any 404 not found errors when installed in Yakkety. But the instructions fail to inform that we need citrain installed and citrain host-upgrade 031 needs to be run with sudo. An example of how developers are not seeing things from the point of view of an ordinary user with a default install of Ubuntu.

```
sudo apt install phablet-tools-citrain
sudo citrain host-upgrade 031
```

And it still loads to a black screen on Nvidia-Nouveau. A lot of work will have to be done otherwise there will be a lot of complaints from ordinary users come the autumn. Or should I say "the fall?" 

Regards.

Again .. I see it as an exclusive venture at the moment as I certainly cannot get citrian code to operate on my high_end equipment. You're not alone.

---

### Post by danc-dccathome on 2016-05-10
I get this after running those commands:
```
dcihon@dcihon-ubuntu-testing:~$ sudo apt install phablet-tools-citrain
[sudo] password for dcihon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phablet-tools-citrain is already the newest version (1.2+16.10.20160504-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dcihon@dcihon-ubuntu-testing:~$ sudo citrain host-upgrade 031
/usr/bin/citrain: 45: .: Can't open /usr/share/phabletutils/shell-adb-common.sh


```

---

### Post by ventrical on 2016-05-11
> **danc-dccathome said:**
> I get this after running those commands:
```
dcihon@dcihon-ubuntu-testing:~$ sudo apt install phablet-tools-citrain
[sudo] password for dcihon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phablet-tools-citrain is already the newest version (1.2+16.10.20160504-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dcihon@dcihon-ubuntu-testing:~$ sudo citrain host-upgrade 031
/usr/bin/citrain: 45: .: Can't open /usr/share/phabletutils/shell-adb-common.sh


```

From what I understand so far, ci-train is using a silo for for touch . As I said previously. I am not sure exactly what kind of desktop Michael is talking about. I do not think it applies to standard amd64 desktop.. however the information provided  tells us nothing of the equipment he is using.

regards..

---

### Post by ventrical on 2016-05-11
From mhall blog:

> 
I'm an app reviewer for the store, so I have access to download them  from the admin interface. Sadly that won't be an option for most people.

Some others I had built locally already, so I just found the .click I already had and installed it&#65279;.

eof>

regards..

---

### Post by ventrical on 2016-05-11
I sent this request to mhall:

> 
Michael,

We at ubuntuforums are curious as to the full specs of  the hardware you are sing to run unity8. There is no information on this  with exception of Intel GPU. Are you using flat out amd64 arcitechture?

Regards.. ventrical


edit:

also looks like those who have had some success are using laptops. For developers, probably state of the art form factors. I think I just interfected two good installs  by downloading the ppa onto my towers .. but thats biusness on the edge :)

---

### Post by ventrical on 2016-05-11
I removed the ppa and got my unity8 on yakkety back with working browser .. which I am wrting this message from now. So I'll do 10 days of dogs-breakfast of unity8 on yakkety and you guys go ahead with dogs-breakfast on xenial:)

Regards..

---

### Post by ventrical on 2016-05-12
from mhall blog:

Hardware:

ventrical: What kind of hardware?

```

+[ventrical100]("https://plus.google.com/105451416262325831274") It's a pretty standard Lenovo x220, i3 running i386 Ubuntu&#65279;

```

@graham
btw.. his install finally broke..

---

### Post by grahammechanical on 2016-05-12
> btw.. his install finally broke.. :) :)

"I like when a plan comes together." ;)

EDIT: His machine has Intel HD Graphics 3000. He is disqualified! The machine has performance enhancing medication.

---

### Post by ventrical on 2016-05-12
hehehehehehe ..

Regards...


 umm I am going to try the i386 spin  later.

---

### Post by ventrical on 2016-05-17
I got the i386 spin (yakkety-daily) and am going to give it a go on nVidia. Mark is using yakkety and not xenial. Maybe we can find some bugs using i386.

Regards..

---

### Post by ventrical on 2016-05-17
Everything went good on my nVidia box but apps will not stay loaded.

Trying to get:

```

citrain host-upgrade 031

```

seems to be the wild beast that will not be tamed for us common folks :) 

```

gpg:               imported: 1  (RSA: 1)
OK
+ sudo apt-get update -qq
W: The repository 'http://ppa.launchpad.net/ci-train-ppa-service/landing-031/ubuntu yakkety Release' does not have a Release file.
E: Failed to fetch http://ppa.launchpad.net/ci-train-ppa-service/landing-031/ubuntu/dists/yakkety/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
ventrical@ventrical-System-Product-Name:~$ 

```

so this seems exclusive to xenial code ?

---

### Post by ventrical on 2016-05-25
Today's unity8 updates (on yakkety) gave me a bundle including libertine and libertine scopes. I am overwhelmed!! I am writing this in a new and improved - super fast unity8 with none other than firefox!

Yep .. it's working:)

Regards..

---

### Post by amano on 2016-05-25
That's great. That brings the fun back into testing and computing :D

I have stopped hanging around here for not seeing anything "new" being tested, but now that will change ;)

---

### Post by ventrical on 2016-05-25
> **amano said:**
> That's great. That brings the fun back into testing and computing :D

I have stopped hanging around here for not seeing anything "new" being tested, but now that will change ;)

Keep in mind that it is highly experimental ppa at the moment. (ppas found in earlier posts in this thread and other links). But xmir  compositor .. etc.. has become like lightning with smooth movement and the scroll-mouse wheel now works in both browser and firefox. With libertine, legacy debian apps can be run on top of xmir.. so there is some element of  fun to it all :) Only app working is ff but I think the workability of other apps like gnome-screenshot and gnome-terminal are right around the corner.

Regards..

---

### Post by amano on 2016-05-25
Maybe I am waiting a few months until risking a testing session on my own desktop ;)

Until then I will be lurking around here again, hunting for news!!

---

### Post by mikodo on 2016-06-05
Hey folks,

I'm struggling with comprehending what Ubuntu is doing with all this. Is it something like this:

Mir being the display protocol while keeping XMir functionality untill Unity can go it alone without X and ...

Unity8 being the compositing desktop manager, and display server replacement of X.

Did I get that anywhere close to what is happening?

---

### Post by amano on 2016-06-06
Mir is more than just a protocol. It is the display server!

So MIR equals Wayland+Weston combined. Just for the input stuff it uses the wayland "libinput" library.

---

### Post by grahammechanical on 2016-06-06
My take on all this? Are you ready for it?

The future of Ubuntu was Mir + Unity 8 but all that has changed. The future of Ubuntu is now Snappy Ubuntu core + Mir + Unity 8 + snap apps (AKA, Snappy  Ubuntu Desktop Next). But that is a big, big jump into the future. "It is Ubuntu, Jim, but not as we know it." To mis-quote a fictional Vulcan.

Then someone noticed that snap apps can be made to run on Unity 7. In fact, it might be possible to run snap apps on all the flavours. And also that deb apps can be made to run on Unity 8 in containers by using Xmir and LXC.

So, we move to Ubuntu Desktop Next on impulse power instead of going to warp factor 9. And Canonical does not alienate the developers of the flavours and allows time for snap packaging to become an industry standard.

Regards

---

### Post by mikodo on 2016-06-06
> **amano said:**
> Mir is more than just a protocol. It is the display server!  So MIR equals Wayland+Weston combined. Just for the input stuff it uses the wayland "libinput" library.  Interesting. 

I had actually likened Mir and Unity to Weston and Wayland initially in my post then, thought the better of it and deleted those lines. Then, you used the analogy of comparing to them. I want to link and partially quote good old Carla Shroder over at Linux.com. She being the first person I ever read on how to symblink from ones /home to a data partition. Like I have now with the help of oldfred holding my hand. He even referenced her post later as he helped me set it up. I digress ...  

[https://www.linux.com/news/what-why-and-how-wayland-and-weston-linux](https://www.linux.com/news/what-why-and-how-wayland-and-weston-linux)  

Snippets: 

"Wayland is a display server protocol that is intended to replace the X Window System. A protocol that communicates between a compositor and its clients.

Weston is a compositing Window Manager and display server.   Only a demo for now.  

Compositing window managers are capable of all kinds of special effects coolness, such as 2D and 3D animations, rotation, drop shadows, blurring,  magnifiers, and all kinds of nifty stuff. Some popular compositing window managers are Xfwm, Cairo, KWin (KDE4), Mutter (GNOME 3) and Compiz. KWin  and Mutter have partial Wayland support, with plans for complete suppport. The Enlightenment team have always done amazing work with graphics,  and are also working hard to implement Wayland. Fedora includes Wayland, and is aiming for complete support by Fedora 21. A number of key toolkits  support Wayland: Qt 5, GTK+ 3, and Clutter".  

So, from that end, the other desktops were never in jeopardy if, there is a will to continue them. I actually asked a dev on #xubuntu-devel  a couple of months ago if, it could possible to use Wayland with Xubuntu, (Xfce). His response was "Why not, we will choose the best at the time".    > **grahammechanical said:**
> My take on all this? Are you ready for it?  The future of Ubuntu was Mir + Unity 8 but all that has changed. The future of Ubuntu is now Snappy Ubuntu core + Mir + Unity 8 + snap apps (AKA, Snappy  Ubuntu Desktop Next). But that is a big, big jump into the future. "It is Ubuntu, Jim, but not as we know it." To mis-quote a fictional Vulcan.  Then someone noticed that snap apps can be made to run on Unity 7. In fact, it might be possible to run snap apps on all the flavours. And also that deb apps can be made to run on Unity 8 in containers by using Xmir and LXC.  So, we move to Ubuntu Desktop Next on impulse power instead of going to warp factor 9. And Canonical does not alienate the developers of the flavours and allows time for snap packaging to become an industry standard.  Regards  It has been you, that has always quietened my fears of the flavours being left behind or outside the goodness that Ubuntu is becoming. For that I am very grateful as, I do love Xfce. Interestingly though, I don't see myself wanting to use it exclusively into my 8th decade, (coming soon enough for me). With all that Ubuntu is hoping to achieve, I see its' desktop a perfect fit for an old casual user as I, that will be super secure, with all the newness they are always "pushing the envelope" for, with its' ease of use. Snappy updates are going to be awesome.

To what you "crystal ball gazed" sounds, very exciting. We know that the only thing certain though, is that Ubuntu will change the rules/path as things progress. Mark et al are making this up as they go ...  Now, I just wish they would fix this [bug]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1400580") in Unity8 and I would be set to use Unity untill I drop. It's going to be a good ride.

  Thanks, folks!

---

### Post by ventrical on 2016-06-07
@mikodo

Grahammechanical's synopsises are mostly on the beam. I think , however, that unity8 will be a default flagship entity (as I understand Mark's intentions) with Unity7+ being the #1 (or Commander Riker as Jean-Luc would say) the #1 alternative. If this is not the case then I will have to do some adjusting to  the current desktop bifurcations that we are currently presented with.

Since we are talking about warp factors here  :)  what I think is that this current episode is not impulse power but rather  the capsule has catapulted into the future at an unimaginable speed and is slowly being throttled back - (this is why we are having so many bugs with Libertine and that it still exists as a ppa). My reasoning is this: that developers are working with newer, faster hardware that is far beyond my pay grade to update to. The idea is to eliminate downtime. I understand this and there is good reason for it. As unity8 becomes more stable in the warp stream then they will be able to scale back  and trace back bugs that exist on more standard and mediocre hardware (like some of the older nVidia graphics adapters.) We must remember what Mark said at the last Webinar. That he has 80 persons (developers) working only on  the unity8 desktop. (that singularity if you will). Xubuntu and Lubuntu will pick up the slack and inject longevity into more legacy machines that have limited hardware  capabilities, but, make no bones (no reference to Dr. McCoy) about it, unity8_default will only go so far back on legacy form factors and xmir/unity8-system-compositor will be a demanding child process.

  Mark truly has a penchant for benevolence as he presents through his teams to us, Unity7, Mate, Gnome3, Xubuntu, Lubuntu and of course the snappy project and if this is not enough we still have FVwm-crystal, xmonad and razorqt! to play with:) just to mention a few. (as you have already mentioned most) :)

  The added bonus in all this is that a lot of hardware is dirt cheap. Most motherboards from a decade ago that handle 800MHzDDR2can become a highspeed computer with an added cheap refurbished 120GB SSD drive for 40 bucks! Thats not bad considering. So the price I would pay for current i7 processor I could get  4 machines up and running just as fast.  

 So unity8 will be able to give us the best of both worlds but unity7 will most likely be a reliable fall back for many years to come. But then again , jumping between warp factors could cause some serious jet lag :)

Regards..

---

### Post by grahammechanical on 2016-06-07
Travel at the speed of light and we meet ourselves coming back!

personal_x86.img ran fine on this steam powered machine of mine. It was snappy Ubuntu + Mir built on Wiley code (15.10). True, it is no longer being updated. It has not progressed on to Xenial code but I am going to put in another install of it and see if these new snap apps will run on it. It will all depend on "snap find" making contact with a repository. I am uncertain it will work. I may have to learn how to side load an app.

Regards

---

### Post by ventrical on 2016-06-07
As I recall, some of the major players divulged that they could not wait to get there hands on personal_x86.img in May.. "all the tools are in place" . It's now well into June. I tried what you are about to try a little while back. Thought the same thoughts practically.  It did not work at all. I'll be watching what you do ... and try to emulate. It is just my view at this stage of the game that the Libertine process of running old legacy deb apps on unity8 will save Canonical tons of headaches and this may be the fork in the road less travelled. Good luck, Jim and watch out for those Klingons.

Regards..

---

### Post by ventrical on 2016-06-07
Surprise .. got nautilus to work :)

---

### Post by grahammechanical on 2016-06-07
Another failure. Unable to install any snaps listed in snap find on personal_x86. To start with personal_86 uses snappy install as the command and not snap install. And it is not accessing the necessary repository.

Back to the drawing board.

Regards

---

### Post by ventrical on 2016-06-07
I had a big problem here:

```

Setting up snapd (2.0.6) ...
Job for snapd.refresh.timer failed. See "systemctl status snapd.refresh.timer" and "journalctl -xe" for details.
snapd.refresh.timer couldn't start.
Setting up thermald (1.5-2ubuntu2) ...
Setting up unity-control-center-faces (15.04.0+16.04.20160413-0ubuntu3) ...
Setting up upower (0.99.4-2ubuntu0.2) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Setting up libmetacity-private3a:amd64 (1:3.18.4-0ubuntu0.3) ...
Setting up compiz-gnome (1:0.9.12.2+16.04.20160526-0ubuntu1) ...
Setting up compiz (1:0.9.12.2+16.04.20160526-0ubuntu1) ...
Setting up unity (7.4.0+16.04.20160526.1-0ubuntu1) ...
Setting up indicator-bluetooth (0.0.6+16.04.20160526-0ubuntu1) ...
Setting up ubuntu-system-settings (0.4+16.04.20160525-0ubuntu1) ...
Setting up unity8 (8.12+16.04.20160527-0ubuntu1) ...
Setting up unity8-desktop-session-mir (1.0.12+16.04.20160601-0ubuntu1) ...
Setting up unity-control-center (15.04.0+16.04.20160413-0ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for systemd (229-4ubuntu6) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-23-generic
ventrical@ventrical-System-Product-Name:~$ sudo snap install x11-apps
[\] Setup snap "ubuntu-core" security profiles

```

and it just hung for about five minutes... but I didn't touch it.. I just let it be .. went over to another machine and then came back to it and got this:

```

update-initramfs: Generating /boot/initrd.img-4.4.0-23-generic
ventrical@ventrical-System-Product-Name:~$ sudo snap install x11-apps
5.95 MB / 5.95 MB [======================================] 100.00 % 170.53 KB/s 

Name      Version  Rev  Developer   Notes
x11-apps  1        2    chadmiller  -
ventrical@ventrical-System-Product-Name:~$ 

```

so it eventually coughed up a biscuit. This is on an original install the referred to the ppa that mhall is using.. using the 32bit version on xenial. So I am going to try libertine again because this one machine , libertine does nothing.

Hey, graham .. thanks for trying that out. Most likely I will get the same results.

I am wondering if can load a desktop  on snappy-core now with LXD.

regards..

---

### Post by ventrical on 2016-06-15
I am getting freeze ups and htop reports 100% of CPU usage.



[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1592932](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1592932)

---

### Post by amano on 2016-06-20
[https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html](https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html)

The new Unity8 fixes look promising: Cursor fixes and finally no doubled login!! This is starting to feel like a real desktop, doesn't it?

Did this Unity 8.12+ hit the repos yet?

---

### Post by deadflowr on 2016-06-20
> **amano said:**
> [https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html](https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html)

The new Unity8 fixes look promising: Cursor fixes and finally no doubled login!! This is starting to feel like a real desktop, doesn't it?

Did this Unity 8.12+ hit the repos yet?

What I currently see:
```
unity8:
  Installed: 8.12+16.10.20160617-0ubuntu1
  Candidate: 8.12+16.10.20160617-0ubuntu1
  Version table:
 *** 8.12+16.10.20160617-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ventrical on 2016-06-20
I think the game has changed a little since my last update a day or two ago. There is problems with:

```

citrain host-upgrade 031


```

it reports back that the ppa is outdated .. and I have not seen any updates to mhalls original blog so I am thinking that perhaps soon the ppa will no longer be required.

 If you had installed libertine, libertine-scopes and x11-apps in snappy then I think the only way to fix it is with a fresh install because none of the conventional methods of recovery work. The programs can be removed but they have left an imprint and libertine will not *connect* , create or manage containers. So you have a workable standard unity8 but no firefox , nautilus etc... (I did get nautilus, gedit and firefox to work just fine in a container.

 I am about to update a few installs now and create a new one without the ppa... just to see whats up.

:) 

Regards..

---

### Post by ventrical on 2016-06-20
> **deadflowr said:**
> What I currently see:
```
unity8:
  Installed: 8.12+16.10.20160617-0ubuntu1
  Candidate: 8.12+16.10.20160617-0ubuntu1
  Version table:
 *** 8.12+16.10.20160617-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Are you using the ppa  or are you on a dry run from proposed?

Regards..

---

### Post by ventrical on 2016-06-20
> **amano said:**
> [https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html](https://lists.ubuntu.com/archives/yakkety-changes/2016-June/003612.html)

The new Unity8 fixes look promising: Cursor fixes and finally no doubled login!! This is starting to feel like a real desktop, doesn't it?

Did this Unity 8.12+ hit the repos yet?

Absolutely awesome! :)

Cannot copy n paste from terminal .. but ..

edit

btw .. to send up a screenshot use standard method in firefox on ubuntuforums . Since there is only one window you have to click "close this window" at the near top right of the firefox session and you will go back to ubuntuforums edit screen.

Regards..

---

### Post by grahammechanical on 2016-06-20
Unity8 session is still causing me frustration. I have an i386 install of yakkety with Unity 8 session that I have not visited for a few weeks. So, I updated it and tried the Unity 8 session. And there is progress.

I now get the default wallpaper with a top panel that does not have any indicators. The launcher is missing. The scopes scope has a black background without any scopes and the mouse pointer is stuck centre screen.

It is progress on Nvidia hardware but with Nouveau GPU lockup. The whole system is frozen. Things have improved. No double login. 

And so we live.

---

### Post by ventrical on 2016-06-23
On several other form factors using various distros, xenial, yakkety, and64, i386 with nVidia graphics it is almost impossible to get libertine containers to work. Libertine is a shell script  that uses lxc-containers and even the lxc commands in the unity8 terminal will come up with all sorts of errors. I am using a more current yakkety-ubuntu-desktop .iso I am also using the ppa and still following the dogfooding instructions from mhalls blog.

  It is very discouraging to have this libertine tool busted as it is but that's the way the cookies crumble. On a brighter note.. the one install on my Intel graphics hardware could not be  better to work and experiment with.

Regards..

---

### Post by mikodo on 2016-06-23
^^ This remains unfortunate for many. Effectively locking them out of testing.

I hope this doesn't become the de facto support of "development" for the future.

---

### Post by ventrical on 2016-06-23
> **ventrical said:**
> I think the game has changed a little since my last update a day or two ago. There is problems with:

```

citrain host-upgrade 031


```

it reports back that the ppa is outdated .. and I have not seen any updates to mhalls original blog so I am thinking that perhaps soon the ppa will no longer be required.

 If you had installed libertine, libertine-scopes and x11-apps in snappy then I think the only way to fix it is with a fresh install because none of the conventional methods of recovery work. The programs can be removed but they have left an imprint and libertine will not *connect* , create or manage containers. So you have a workable standard unity8 but no firefox , nautilus etc... (I did get nautilus, gedit and firefox to work just fine in a container.

 I am about to update a few installs now and create a new one without the ppa... just to see whats up.

:) 

Regards..

Correction:

X11-apps for Unity8 is installed by default from the ppa.

Beats me.

Regards..

---

### Post by ventrical on 2016-06-23
> **mikodo said:**
> ^^ This remains unfortunate for many. Effectively locking them out of testing.

I hope this doesn't become the de facto support of "development" for the future.

Thanks for your input Mikodo. I don't think it is intentional. I think it is an xmir problem with libertine+nVidia.  I will continue to try and  figure this out and get the correct data.

Regards..

---

### Post by ventrical on 2016-06-23
Current work around for nVidia is to disable nVidia in EFI/Bios and use Intel graphics.

[http://askubuntu.com/questions/770014/unity-8-not-working-with-nvidia-graphics-card](http://askubuntu.com/questions/770014/unity-8-not-working-with-nvidia-graphics-card)

Not very encouraging.

---

### Post by ventrical on 2016-06-23
Well.. it finally happened.  The install of unity8 I had working with firefox, gedit and nautilus in libertine containers finally destroyed itself. Not only that , it completely wiped out my unity8 install.. gone from unity greeter. I rebooted after update and wanted to try another update but something else was pulling in on my bandwidth. After it was over .. no unity8. I got cleaned out lock, stock and barrel.

  I guess it was just too much. I mean .. imagine the security of firefox  running in an lxc container on top of xmir only in this case it was not imagined .. it was real.


sniffle .. boy.. that one hurt..

Regards..

---

### Post by QDR06VV9 on 2016-06-23
> **ventrical said:**
> Well.. it finally happened.  The install of unity8 I had working with firefox, gedit and nautilus in libertine containers finally destroyed itself. Not only that , it completely wiped out my unity8 install.. gone from unity greeter. I rebooted after update and wanted to try another update but something else was pulling in on my bandwidth. After it was over .. no unity8. I got cleaned out lock, stock and barrel.

  I guess it was just too much. I mean .. imagine the security of firefox  running in an lxc container on top of xmir only in this case it was not imagined .. it was real.


sniffle .. boy.. that one hurt..

Regards..

:(Sorry to hear that.

---

### Post by ventrical on 2016-06-23
Tried to re-install unity8. I got it back in the greeter but black screen now.  Perhaps there is some action at the ppa ...

break time :)

edit:

Recovered desktop and items manually but the apps will not work now (as which is par for the course with this development atm) but will try to recover them.

regards..

---

### Post by ventrical on 2016-06-24
New features:

Fortunately it is good to have multiple installs of unity8 to test because when one crashes I can go to another and work there :)

The new feature in firefox is that the 'enlarge screen' macro is working now. This is great for accessibility! (ctrl+shift plus +) :)

There has been some success with nVidia based graphics machines if you originally do the install in an Intel video based form factor but it has broken the scopes on a  few occasions when switching the SSD drive to the other machine and then back again.

Although some of my methods are unorthodox it allows me to see inside of the working of the new unity8. libertine containers and xmir. In my opinion it is very enthusiastic and is rolling  along at a very fast pace , much so that I feel somewhat safe to say that if the pace of improvements continue as they are then I can speculate that unity8 with xmir may be default at the end of this cycle!.

regards..

---

### Post by bregma2 on 2016-06-24
> **ventrical said:**
> Tried to re-install unity8. I got it back in the greeter but black screen now.  Perhaps there is some action at the ppa ...


If you're testing Unity 8 on Yakkety you shouldn't have any PPAs installed, especially ones from ci-train.

If you're testing Unity 8 using Ubuntu 16.04 LTS, the only PPA you should have is the [overlay PPA]("https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/stable-phone-overlay").

Anything else is pretty much guaranteed to break your system in horrible and unspeakable ways sooner or later.

---

### Post by ventrical on 2016-06-24
> **bregma2 said:**
> If you're testing Unity 8 on Yakkety you shouldn't have any PPAs installed, especially ones from ci-train.

If you're testing Unity 8 using Ubuntu 16.04 LTS, the only PPA you should have is the [overlay PPA]("https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/stable-phone-overlay").

Anything else is pretty much guaranteed to break your system in horrible and unspeakable ways sooner or later.

Tried that  and Libertine will not work. There is a bug fix commit coming down the pipe soon for libertine. The current testing standard is to use both ppas and expect breakage.

regards..

---

### Post by grahammechanical on 2016-07-14
And then there is this. Note the recommendation to install the ci-train PPA. The blog post is from 4th July.

[https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/](https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/)

Regards

---

### Post by ventrical on 2016-07-14
@graham

Nice find! :)

..quoting from: 
[https://bregmatter.wordpress.com/](https://bregmatter.wordpress.com/)

> 
Underneath the shell layer is a new kind of way of running the  fundamental operating system, with a read-only system image that can be  transactionally updated.  While that is a technical description of how  things differ from the old DOS and Unix way, what it means in practice  is that it’s very difficult to install malware that will take over your  system and turn it into a spambot for some nefarious organization and  it’s also difficult to get your system into a state in which it no  longer boots up or runs improperly.  In the hostile world of today’s  always-on always-connected devices, that’s a very good thing.  Also, no  reinstalling the OS every few months when it starts to crawl, for those  of you out there familiar with Microsoft Windows.

The above sums up a not so far fetched convergence concept in progress. It is also much more that that. The desktop itself so far is much faster with xmir. With x11apps one can really start having fun.

  I have have varied results. I can run debian apps like nautilus, gedit and firefox and I can do it from across different containers. However .. on some installs  (with proposed enabled) I can completely loose all my scopes but still run the xapps that were already installed in the libertine containers. It's not  waste of time to try testing different fresh installs. On some machines .. yes , it can be frustrating but when you get a good , working install it is worth the effort.

Regards..

---

### Post by ventrical on 2016-07-14
This bug fix has been released: [https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020) but that fix alone does not correct all the libertine problems currently. There are still problems with older machine , i.e. nVidia-graphics but the generic unity8 will still work .. just not with containers atm.

Regards..

---

### Post by amano on 2016-07-22
A new Libertine appeared in the repo. I wonder if that is a usable version.

---

### Post by ventrical on 2016-07-23
Yes. There is an recent upgrade of the packages but containers are far from working at this stage. It is behaving more like a "tease" (a term they use is in broadcast journalism) at the moment. It was working fine until they excluded using one of  the ppas.

 It will come up .. look like you have set your legacy container and then it will crash as it did when  the first sessions came out. There are probably some tweaks for this.

There is a lot of work being done on this because libertine/containers will be the new hallmark security  for legacy deb apps so there will most likely be a lot of breakage in the ensuing months.

Regards..

---

