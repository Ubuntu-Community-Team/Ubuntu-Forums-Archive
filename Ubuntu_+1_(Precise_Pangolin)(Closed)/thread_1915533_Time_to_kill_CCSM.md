---
title: "Time to kill CCSM?"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jbicha on 2012-01-26
Should CCSM be in the Precise archives as buggy as it is?

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html)

---

### Post by lucazade on 2012-01-26
it should not be present in archive.. way too buggy.
time to kill it!

---

### Post by ronacc on 2012-01-26
why not FIX it instead ?

---

### Post by EgoGratis on 2012-01-26
> **jbicha said:**
> Should CCSM be in the Precise archives as buggy as it is?

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html)

No i don't agree Compiz is more then just Unity. Where would user set other Compiz settings? If user will find all Unity settings in System Settings then i don't see any dilemma because most users will use System Settings anyway and remember why all the users used CCSM in the first place that is because Unity was set default and didn't provide Unity settings in System Settings!

Better than removing CCSM from the users to use would be to fix Compiz Cube for example!

If CCSM is removed we will just end up having PPA for CCSM and use that instead? If disabling Unity in CCSM is such problem then when disabling it there should be dialog THIS WILL BREAK UNITY USE UNITY -- RESET to repair. Proceed? Yes / No. And yes unity --reset did always fixed Unity for me and i didn't have to do nothing else manually!

---

### Post by fjgaude on 2012-01-26
As Ubuntu gets on TVs, into cell phones and tablets, and stays on the desktop, surely both CCSM and some cut-down of Compiz is warranted. <smile>

Brace ourselves, HUD is on its way.

---

### Post by dino99 on 2012-01-26
Good question as ccsm is so buggy and does not have been received fixes since ages. So time has comes to replace it by the needed tool settings to include into dconf for example.

---

### Post by kansasnoob on 2012-01-26
> **EgoGratis said:**
> No i don't agree Compiz is more then just Unity. Where would user set other Compiz settings? If user will find all Unity settings in System Settings then i don't see any dilemma because most users will use System Settings anyway and remember why all the users used CCSM in the first place that is because Unity was set default and didn't provide Unity settings in System Settings!

Better than removing CCSM from the users to use would be to fix Compiz Cube for example!

If CCSM is removed we will just end up having PPA for CCSM and use that instead? If disabling Unity in CCSM is such problem then when disabling it there should be dialog THIS WILL BREAK UNITY USE UNITY -- RESET to repair. Proceed? Yes / No. And yes unity --reset did always fixed Unity for me and i didn't haven to do nothing else manually!

I rather like most of what you're saying here, but I generally prefer Metacity to Compiz anyway. Preferences aside how would we deal with "the cube", "wobbly windows", etc, etc without CCSM?

Most of the early testers here know that I'm pursuing a shortcut to "fallback/classic" but for Oneiric I focused entirely on Metacity. For Precise I hope to provide some basic info for Compiz.

I spoke out against including Ubuntu-tweak in the repos on Ayatana in favor of My-Unity being included in the repos, but if we're going to axe CCSM I wonder :confused:

---

### Post by EgoGratis on 2012-01-26
Just one more thought.

-CCSM is so buggy that all users had to use it for two Ubuntu releases.
-CCSM is so buggy that now when GUI for Unity (not Compiz) options exist user should not be able to install it from USC.

---

### Post by EgoGratis on 2012-01-26
> I rather like most of what you're saying here, but I generally prefer Metacity to Compiz anyway.

Won't Compiz replace Metacity in the future? Wasn't it replaced with Mutter in Gnome 3? Will Compiz be used in the future releases or it will be replaced and with what if it will be?

---

### Post by Simian Man on 2012-01-26
Buggy software makes up a large portion of Debian and Ubuntu's repositories.  Why make an exception for CCSM?

---

### Post by effenberg0x0 on 2012-01-26
CCSM should die, no question about it. The problem is that if it's killed too soon, we will have to post if [[ $(gconftool-2 --get yadayadayada) == "something" ]]; then gconftool-2 --set yadayadayada etc etc command lines all over this forum every time someone needs to enable/disable/configure a plugin...  Realistically, a handful of the helpers are capable of  it IMO. So, a premature kill of CCSM could cause more trouble than benefit. I hope it's killed only when its replacement is capable of doing at least as much as CCSM currently can.

---

### Post by EgoGratis on 2012-01-26
Will Compiz in the future releases differ form Compiz we use now? Will Compiz in future releases be replaced by something else? i don't know but until Compiz like we know it now exist there should be GUI tool to change settings in USC? It would be step back to have the same Compiz and not to have GUI for settings in USC?

If Compiz will be changed in future releases then GUI can change to? If Compiz will be used only for Unity then CCSM wold be not used anymore and that would be it but having Compiz with all these features by default and removing GUI to set them from USC is in my opinion not good. And a lot of users used CCSM for setting Unity not the Compiz and i guess the "fear" for braking things with CCSM will diminish now other ways of setting Unity (not Compiz) will soon be available?

---

### Post by rg4w on 2012-01-26
> **Simian Man said:**
> Buggy software makes up a large portion of Debian and Ubuntu's repositories.  Why make an exception for CCSM?
Agreed.  Flag it with a warning, but leave it in.  CCSM is currently the only method available for users to tailor Unity to resolve a wide range of preferences and usability issues.

If the proposal were to put ALL of the relevant CCSM settings in some new config GUI I'd support this.

But the very limited subset of options in the Unity plugin don't address many important issues, such as altering the Maximize behavior.

Whether we like it or not, CCSM is currently an essential tool.

---

### Post by effenberg0x0 on 2012-01-26
This is not something I follow closely but:
> **EgoGratis said:**
> Will Compiz in the future releases differ form Compiz we use now? 
Supposedly, ours is already causing trouble to other desktops (*I can't confirm this information*). But, anyway, yes. Compiz is being updated and fixed. And, eventually, it was supposed to be rewritten for Wayland.

> **EgoGratis said:**
> Will Compiz in future releases be replaced by something else?   
Supposedly (again, I have no clue, schedule, etc), yes. It should be rewritten to be compatible with Wayland, so it's a whole new thing. [/quote]

> **EgoGratis said:**
> 
i don't know but until Compiz like we know it now exist there should be GUI tool to change settings in USC? It would be step back to have the same Compiz and not to have GUI for settings in USC?
They are migrating a couple settings to gnome-control-center, as we expected here, but I really doubt they will go through the trouble of recreating all options, for all plugins. The overall idea, as it seems, is that too much config increases the chance of average users destroying their desktops. IMO, a developer in search of fame and with a lot of free time will create a nice Python GUI to absorb all (or most) of CCSM capabilities (MyUnity?).

Regards,
Effenberg

EDIT: Or someone with a more straightforward approach will just throw in the forum a bash script that does it all in a cli way.

---

### Post by philinux on 2012-01-26
If this carries maybe ccsm will not be needed as much.

 [http://www.omgubuntu.co.uk/2012/01/precise-adds-new-unity-configuration-options/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/precise-adds-new-unity-configuration-options/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by EgoGratis on 2012-01-26
> They are migrating a couple settings to gnome-control-center

Unity settings (not Compiz).

> Compiz is being updated and fixed. And, eventually, it was supposed to be rewritten for Wayland.

Yes, some things will probably change in the future releases. I did read the blog post about problems with Compiz development, but in general i don't have problems with Compiz.

But i agree completely. If Compiz needs to change for future releases OK i understand that. But for now is Compiz with a lot of features enabled by default and if the only step would be to take the GUI to change this features away this would be step back.

---

### Post by thatguruguy on 2012-01-26
It needs to be mentioned that the debate is not about whether to remove Compiz, but whether to remove CCSM (Compiz-Config Settings Manager).  I haven't seen anyone arguing that Compiz needs to be removed, just the (advanced) tool for dealing with it.

The argument goes further, that the settings in the MyUnity tool be expanded to deal with the most common use cases than can currently only be dealt with in CCSM.

---

### Post by EgoGratis on 2012-01-26
> **philinux said:**
> If this carries maybe ccsm will not be needed as much.

 [http://www.omgubuntu.co.uk/2012/01/precise-adds-new-unity-configuration-options/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/01/precise-adds-new-unity-configuration-options/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

Yes but this is the problem Unity is not Compiz. Where would you set Compiz settings (not Unity).

---

### Post by effenberg0x0 on 2012-01-26
I think that basic stuff, like Number of Desktops, will be available. But I wouldn't expect them to have settings for animations, wobbling windows, etc. They'll leave that to third party developers IMO.

---

### Post by EgoGratis on 2012-01-26
> **thatguruguy said:**
> It needs to be mentioned that the debate is not about whether to remove Compiz, but whether to remove CCSM (Compiz-Config Settings Manager).  I haven't seen anyone arguing that Compiz needs to be removed, just the (advanced) tool for dealing with it.

The argument goes further, that the settings in the MyUnity tool be expanded to deal with the most common use cases than can currently only be dealt with in CCSM.

Probably the real debate here is do we need Compiz (not Unity) with so many features or not? 

My opinion is that until that gets decided/changed we need CCSM in USC.

---

### Post by thatguruguy on 2012-01-26
> **EgoGratis said:**
> Probably the real debate here is do we need Compiz (not Unity) with so many features or not? 

My opinion is that until that gets decided/changed we need CCSM in USC.

It strikes me that to the extent that there is a debate over our need of Compiz, it's a debate that you've raised.  It wasn't the issue presented in this thread, nor the issue in the listserv discussion that this thread refers to.

---

### Post by philinux on 2012-01-26
> **EgoGratis said:**
> Yes but this is the problem Unity is not Compiz. Where would you set Compiz settings (not Unity).

To clarify, I meant for unity only.

---

### Post by VinDSL on 2012-01-26
I don't know if you guys have seen it, read about it, and/or are using it, but...

They have recently added a package (to one of the repos) called, MyUnity.

I'm running PepperMint OS right now (from a 16GB thumb drive) otherwise I'd toss you a screenie of it.

It does everything that I normally use CCSM for... except borderless windows on my browsers.

Word has it, that Canonical is going to add it to the official Precise repos when 12.04 is released.

Anyway, check it out...

```
sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update
sudo apt-get install myunity
```

I installed it via Synaptic, so it might already be sitting in yours, depending on which repos you're using.

---

### Post by philinux on 2012-01-26
> **VinDSL said:**
> I don't know if you guys have seen it, read about it, and/or are using it, but...

They have recently added a package (to one of the repos) called, MyUnity.

I'm running PepperMint OS right now (from a 16GB thumb drive) otherwise I'd toss you a screenie of it.

It does everything that I normally use CCSM for... except borderless windows on my browsers.

Word has it, that Canonical is going to add it to the official Precise repos when 12.04 is released.

Anyway, check it out...

```
sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update
sudo apt-get install myunity
```

I installed it via Synaptic, so it might already be sitting in yours, depending on which repos you're using.

I've had it as a link in my Sig for ages. It does the job. Ideally unity settings would be better off outside ccsm IMHO.

And its too easy to screw it all up enabling the cube etc. That needs fixing.

---

### Post by castrojo on 2012-01-26
> **VinDSL said:**
> Word has it, that Canonical is going to add it to the official Precise repos when 12.04 is released.


It's already in 12.04, which is why we don't need CCSM.

---

### Post by philinux on 2012-01-26
> **castrojo said:**
> It's already in 12.04, which is why we don't need CCSM.

What about the peeps who don't want to use unity, they want gnome session fallback and still want ccsm.

---

### Post by castrojo on 2012-01-26
It's just as buggy, and either way if you know you want the fallback session you probably know how to add a PPA (if someone makes one). Either way the tool is broken and should be removed unless someone fixes it.

EDIT: Doesn't the fallback session use metacity?

---

### Post by ventrical on 2012-01-26
> **castrojo said:**
> It's just as buggy, and either way if you know you want the fallback session you probably know how to add a PPA (if someone makes one). Either way the tool is broken and should be removed unless someone fixes it.

EDIT: Doesn't the fallback session use metacity?
ccsm works good on some machines and not others. I don't see the sense in killing it. Canonical wants 200 million users by the time Precise is released (or just afer that. Good luck , if ccsm is gone.

Also - Myunity !?? :) Looks like the McDonalds Golden Arches.  They got to do somthing about that.

---

### Post by effenberg0x0 on 2012-01-26
A Confession: 
Despite mc4man's many attempts and best-efforts to explain me the ccsm profiles vs wild $COMPIZ_CONFIG_PROFILE thing, why it worked and then suddenly it didn't work any more, and then it worked again, but not for long, unless something else, etc, I gotta confess that I never really got it. I'm ccsm-impaired.

So I don't care much if they are gonna go dconf, gconf, json, xml, whatever but, as long as it's not compizconfig-backend-<something-broken> I think life will be easier (for me at least!) :) That's a good thing I hope to see of this move from ccsm to gnome-control-center. 

A question: 
If I write a new Compiz Plugin, say FlyingWatermelons. Where will users load my Settings Dialog (Number, speed of watermelons)? Suppose I can't count on ccsm being in the repos, so I'll write a Python something to load a Settings Program/Window for my plugin. Great, done. Then someone else writes a new plugin too. Let's say LoudContinuousUnbearableScreams. So, that's a new Python Settings Program/Window? 
Or are all plugins gonna hack their way into gnome-control-center? Or will all of them depend on third part apps for setup?

---

### Post by castrojo on 2012-01-26
> **ventrical said:**
> ccsm works good on some machines and not others. I don't see the sense in killing it.

That's exactly why it should be removed, it's too unreliable for too many people.
 
> 
Also - Myunity !?? :) Looks like the McDonalds Golden Arches.  They got to do somthing about that.

Yeah but it works, and the UI isn't perfect, and seriously, the UI in ccsm is the worst thing ever.

---

### Post by ventrical on 2012-01-26
> **castrojo said:**
> That's exactly why it should be removed, it's too unreliable for too many people.
 


Yeah but it works, and the UI isn't perfect, and seriously, the UI in ccsm is the worst thing ever.

 But what irks me is that  ccsm mainly became unreliable with the introduction of Unity and the Unity Plugin - way back in Natty. It worked just great on newer and older machines alike with Lucid and Maveric (still does) I mean who wants to get rid of a hallmark linux application (ccsm) because it won't jive  with  noobUnity Desktop Environment ?  It seems to me that the writers of the Unity 3D interface had decided to used mixed and matched patched code that hooked into COMPIZ rather than actually write code that did not have to be hooked to COMPIZ. So rather than do the extra work here  they throw together a plugin  effectively neutering ccsm which has been a workhorse in the eyecandy mareteering aspect of recruiting new users to the Ubuntu OS. So for older noobs and younger noobs alike it then becomes a long and extremely boring session at the terminal. Vista was unreliable and then ... nevermind .. sorry for going there.

  it's just my opinion but I think that somebody has to really sit down and take a good look at the Unity flowchart and Compiz (ccsm) flowchart and try to pinpoint the erratic code that ius causing all the problems .. or is it just an easier and softer way to obsolete ccsm alltogether because a Unity code rewrite would just be too difficult at this stage of the game?

  I am just assuming but I think that  just too many resources have been spent on tweaking the Unity DE and a lot of legacy bugs and other projects are being swept under the carpet once again..

---

### Post by EgoGratis on 2012-01-26
But let say CCSM is removed from USC and there will be no PPA. How would you set up Compiz?

---

### Post by ventrical on 2012-01-26
> **EgoGratis said:**
> But let say CCSM is removed from USC and there will be no PPA. How would you set up Compiz?

Then it would be like a pre-set  hands-off core or they would eventually morph myunity into an adjustable emulation of a reasonable facsimile of ccsm ! Hey .. there ya go !

---

### Post by effenberg0x0 on 2012-01-26
> **EgoGratis said:**
> But let say CCSM is removed from USC and there will be no PPA. How would you set up Compiz?

gconftool-2 -R /apps/compiz-1/plugins to list available plugins, keys, values.
gconftool-2 set /apps/compiz-1/plugins/SomePlugin/SomeKey --type SomeType 'value'

Easier hun?

---

### Post by lucazade on 2012-01-26
> **EgoGratis said:**
> But let say CCSM is removed from USC and there will be no PPA. How would you set up Compiz?

Sane default settings and no need for customization tool. IMHO

---

### Post by EgoGratis on 2012-01-26
>  they would eventually morph myunity into an adjustable emulation

Who, which Compiz settings exactly and when? If Compiz needs to be "slimed down" i understand this but to have the same Compiz in Ubuntu 12.04 and take away 96% of the settings? I just don't understand this and if some other GUI tool for Compiz not just Unity settings will be available in USC cool and will be "much better" what is the point then?

---

### Post by castrojo on 2012-01-26
> **ventrical said:**
> It worked just great on newer and older machines alike with Lucid and Maveric (still does) I mean who wants to get rid of a hallmark linux application (ccsm) because it won't jive  with  noobUnity Desktop Environment ?

I've never seen this tool "work great", and I would hardly call a window full of random checkboxes a hallmark linux application.


> So rather than do the extra work here they throw together a plugin  effectively neutering ccsm which has been a workhorse in the eyecandy mareteering aspect of recruiting new users to the Ubuntu OS.

Good! Most of those plugins don't work or are unmaintained, and let's be realistic here, using ccsm as a tool to recruit new users? 

> Vista was unreliable and then ... nevermind .. sorry for going there.

Vistas configuration tool doesn't break your desktop like ccsm does.

> it's just my opinion but I think that somebody has to really sit down and take a good look at the Unity flowchart and Compiz (ccsm) flowchart and try to pinpoint the erratic code that ius causing all the problems 

ccsm has been broken for multiple releases, obviously no one cares to fix it, why should we ship it then?

> I am just assuming but I think that  just too many resources have been spent on tweaking the Unity DE and a lot of legacy bugs and other projects are being swept under the carpet once again.

We have real bugs and crashers we should be fixing, not corner case dice-roll bugs from an unmaintained tool.

---

### Post by ventrical on 2012-01-26
> **effenberg0x0 said:**
> gconftool-2 -R /apps/compiz-1/plugins to list available plugins, keys, values.
gconftool-2 set /apps/compiz-1/plugins/SomePlugin/SomeKey --type SomeType 'value'

Easier hun?


Then why have any GUI desktop at all? Just hit <Ctrl+Alt+F1> and do everything from terminal. Why even have  GUI or any assistive technologies?  Make Ubuntu Unity an exclusive club for linux whizzes only.

---

### Post by philinux on 2012-01-26
What about the desktop zoom for accessibility and me of course. You know super  and mouse wheel roll.

---

### Post by effenberg0x0 on 2012-01-26
> **ventrical said:**
> Then why have any GUI desktop at all? Just hit <Ctrl+Alt+F1> and do everything from terminal. Why even have  GUI or any assistive technologies?  Make Ubuntu Unity and exclusive club for linux whizzes only.

Hey dude, calm down :) What I mean is that CCSM is just a frontend to read/write to gconf using basically those 2 commands I posted more or less (via an API, but it doesn't really matter). So it's irrelevant if ccsm exists or not, is included or not, if Canonical will put it into gnome-control-center or not because one can still load and setup plugins. Given how easy it can be done with a couple commands to gconf, one can create an easy to use CLI or GUI interface for it using mostly anything: bash, C, python, etc. I strongly doubt there won't be other GUI alternatives to setup compiz-plugins options very soon.

---

### Post by EgoGratis on 2012-01-26
> gconftool-2 -R /apps/compiz-1/plugins to list available plugins, keys, values.
gconftool-2 set /apps/compiz-1/plugins/SomePlugin/SomeKey --type SomeType 'value'

Easier hun?

For 200 millions users? Do you honestly think 99% of the settings Compiz (not Unity) supports will be of any value to the average user this way? The answer is NO.

> Sane default settings and no need for customization tool. IMHO

For something at scale of one Compiz plugin for example Unity i agree but for something the scale of Compiz with all the features it provides this is just not possible.

It is pointless to have Compiz at this scale then in Ubuntu!

Choose what features you want in Ubuntu and remove the rest then, because it is useless to run such feature rich compositor if 1% of user will know hot to set it up and use the features.

---

### Post by effenberg0x0 on 2012-01-26
Meh, I give up.

---

### Post by castrojo on 2012-01-26
> **philinux said:**
> What about the desktop zoom for accessibility and me of course. You know super  and mouse wheel roll.

That's a very valid point, it's sad we don't have that in the accessibility tools to begin with. :(

---

### Post by pajn on 2012-01-26
As CCSM is the only structured (sort of anyways) and simple way to control Compiz settings (Compiz is more than Unity you know) it can't be removed.

I don't realy understand why it would be such a bad thing to have it in the repo?

Sure it shouldn't be included on the CD but it isn't and there is no such plans either.

---

### Post by EgoGratis on 2012-01-26
If things in the long run will be better with slimming down Compiz or doing thing differently then this is the way to do it. But then cut deeper and do what must be done in one step.

Do a list what will stay supported (in addition to Unity) and make GUI settings available to the user and that is that. Taking away just GUI settings doesn't do much in terms of making things better.

---

### Post by castrojo on 2012-01-26
> **pajn said:**
> As CCSM is the only structured (sort of anyways) and simple way to control Compiz settings (Compiz is more than Unity you know) it can't be removed.

CCSM isn't simple!

> I don't realy understand why it would be such a bad thing to have it in the repo?

Because it breaks people's computers. We don't think or guess that it breaks people's computers, we know it does.

---

### Post by philinux on 2012-01-26
> **castrojo said:**
> That's a very valid point, it's sad we don't have that in the accessibility tools to begin with. :(

Indeed, glad you agree. It's not enabled in ccsm by default either.

---

### Post by effenberg0x0 on 2012-01-26
> **EgoGratis said:**
> If things in the long run will be better with slimming down Compiz or doing thing differently then this is the way to do it. But then cut deeper and do what must be done in one step.

Do a list what will stay supported (beside Unity) and make GUI settings available to the user and that is that. Taking away just GUI settings doesn't do much in terms of making things better.

That's the real problem. CCSM or not, there are ways to use and set current plugins. GUIs to control such plugins/settings will be done because they are easy to do. But many plugins are totally/partially broken and unmaintained. How are we gonna find enough people to fix plugins and keep them working? (long-term)

---

### Post by ventrical on 2012-01-26
> **castrojo said:**
> I've never seen this tool "work great", and I would hardly call a window full of random checkboxes a hallmark linux application.

 I can get 99% of the features working , even on older machines .. and I can prove it, at least with Lucid and Maveric and in many cases , Natty under Edubuntu.



> 
Good! Most of those plugins don't work or are unmaintained, and let's be realistic here, using ccsm as a tool to recruit new users? 

My apologies here - I meant to say "attract".


> 
Vistas configuration tool doesn't break your desktop like ccsm does.

No, it just busts your whole PC.

 
> 
ccsm has been broken for multiple releases, obviously no one cares to fix it, why should we ship it then?

Point well taken, but I beg to differ on the reasons why. Having bad initial video card detection and the installation of wrong drivers is not a reflection on compiz or ccsm. This is indicative that there is something deeper at large in the framework.


> 
We have real bugs and crashers we should be fixing, not corner case dice-roll bugs from an unmaintained tool.

Fair enough .. but  then it is totally unrealisitc that the announced goal of 200 million users will be  achieved as it was pronounced by Mark Shuttleworth.  Killing ccsm, compiz and Gnome Classic effectively renders Mr. Shuttleworths' hopes and aspirations - a pipe dream.   Please do not get me wrong. I am not a Unity hater. I think it is great. It is really easy on my eyes. My point of veiw really is , that I think Unity with Compiz and ccsm is better !!

---

### Post by arpanaut on 2012-01-26
I've been using My Unity on one of my test installs and it works for the most part, BUT
Lately every time I open it the settings I have are reset to defaults.  (will go bug hunting soon)
Automaximize value needs to be included!  (I never, ever want any window to open maximized; I want control!)
Also the trigger/control for revealing the launcher needs to be included.

My Unity is a good beginning, but needs expanding capabilities.
If ccsm is removed where would one change the number of desktops etc, for example I prefer 4x1 rather than 2x2.
I'm sure everyone has their own personal tweak, this is going to be interesting.

---

### Post by ventrical on 2012-01-26
> **arpanaut said:**
> I've been using My Unity on one of my test installs and it works for the most part, BUT
Lately every time I open it the settings I have are reset to defaults.  (will go bug hunting soon)
Automaximize value needs to be included!  (I never, ever want any window to open maximized; I want control!)
Also the trigger for revealing the panel needs to be included.

My Unity is a good beginning, but needs expanding capabilities.
If ccsm is removed where would one change the number of desktops etc, for example I prefer 4x1 rather than 2x2.
I'm sure everyone has their own personal tweak, this is going to be interesting.


 And there might be depend problems with Cairo-Dock if they pull the plug on Compiz - so they might as well dump Cairo too, and who knows what else will have to go.  Whatever the case , it will be a real Mardi Gras :)

---

### Post by rg4w on 2012-01-26
For the sake of usability, pull CCSM from the USC.

But for the sake of utility, leave it in the PPA.

Once an alternative exists which offers as much control over relevant settings, then CCSM can be safely removed from the archives as well.

And until then, by removing it from the USC it limits its audience to those who know what it is and where to find it.

This would seems to satisfy all the posts thus far, no?

---

### Post by ventrical on 2012-01-26
> **effenberg0x0 said:**
> Hey dude, calm down :) What I mean is that CCSM is just a frontend to read/write to gconf using basically those 2 commands I posted more or less (via an API, but it doesn't really matter). So it's irrelevant if ccsm exists or not, is included or not, if Canonical will put it into gnome-control-center or not because one can still load and setup plugins. Given how easy it can be done with a couple commands to gconf, one can create an easy to use CLI or GUI interface for it using mostly anything: bash, C, python, etc. I strongly doubt there won't be other GUI alternatives to setup compiz-plugins options very soon.


 It's really very simple dude :)

 But try to sell it on 100 million noobs... :)

---

### Post by effenberg0x0 on 2012-01-26
> **ventrical said:**
> It's really very simple dude :)

 But try to sell it on 100 million noobs... :)

Ah, let OMG Ubuntu / Webupd8 do that :P But, meanwhile, let's make money with it. 
I'm accepting calls to remotely install and setup a beautiful cube. USD25/side :) [SIZE=1][COLOR=Gray](minimum 6 sides)[/COLOR][/SIZE]

---

### Post by ventrical on 2012-01-26
> **rg4w said:**
> For the sake of usability, pull CCSM from the USC.

But for the sake of utility, leave it in the PPA.

Once an alternative exists which offers as much control over relevant settings, then CCSM can be safely removed from the archives as well.

And until then, by removing it from the USC it limits its audience to those who know what it is and where to find it.

This would seems to satisfy all the posts thus far, no?

  This  would probably be a good idea for Precise in the long run as long as ccsm wasn't  removed or dumped from earlier version repos. I mean .. come to think of it , I have to admit I am grateful for the heads up about ccsm possible getting ripped from the repos so I can lock some systems I have because ccsm has rarely failed here (even on Precise).

 It has been a great tool to get newcommers started on Linux, Ubuntu especially. I know there is a lot more to Ubuntu but the Compiz tools have a way of capturing one's attention span at least for a few seconds longer so that you may be able to  have the extra time to encourage a new_user to stick around .

  If you want to loose a new_user real quick .. just start talking in sudo ! :)

---

### Post by ventrical on 2012-01-26
> **effenberg0x0 said:**
> Ah, let OMG Ubuntu / Webupd8 do that :P But, meanwhile, let's make money with it. 
I'm accepting calls to remotely install and setup a beautiful cube. USD25/side :) [SIZE=1][COLOR=Gray](minimum 6 sides)[/COLOR][/SIZE]


aheaheaehahe :)

---

### Post by ventrical on 2012-01-26
"we want to deliver something to the audience that really rocks their world"

Mark Shuttleworth

[http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related](http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related)

Rock on...

---

### Post by rg4w on 2012-01-26
> **ventrical said:**
> I have to admit I am grateful for the heads up about ccsm possible getting ripped from the repos so I can lock some systems I have because ccsm has rarely failed here (even on Precise).
Same here.  I can imagine how careless use or unusual systems can cause CCSM to go awry, but here I've played with it long and hard and I've only managed to get one freeze, which occurred while connected to a projector so it's uncertain if the source of the problem was CCSM or my NVidia driver.   In all other cases CCSM has held up like a champ for me - provided I pay attention to the conflict warnings and act appropriately.  In that regard, it's no worse than having Terminal available.

> It has been a great tool to get newcommers started on Linux, Ubuntu especially. I know there is a lot more to Ubuntu but the Compiz tools have a way of capturing one's attention span at least for a few seconds longer so that you may be able to  have the extra time to encourage a new_user to stick around .For myself, it's the *result* I get with CCSM that get people's attention; CCSM itself is an ugly way to get those results, not something I would recommend for newcomers once the Unity plugin options find their way into System Settings.

But until something else exists which offers the same degree of control over as many relevant options, I see no harm in leaving it available from apt-get where those who want it will know how to get it.

The advent of Unity has changed many Compiz settings beyond the scope of Unity's UI elements themselves.   For example, in 11.10 we have the new auto-maximize behavior which may be beneficial to some, but has been a source of annoyance among many Ubuntu fans I've met.  If Canonical's rigorous usability testing showed that the defaults for this behavior are optimal for a majority of their audience I can't find fault with those defaults, but it would be at best risky to assume that those defaults are best for everyone.   CCSM allows the user to change that, but I haven't yet seen anything else which does.

Most of the many comments in this forum and across the web criticizing Unity have done so not in wholesale rejection of the goals Unity seeks to address, but with the details of how it seeks to meet those goals.  Providing a way for the user to adjust the details to their liking would eliminate most complaints about it.

CCSM isn't the answer for that for many reasons, not the least of which is a UI that makes people scream in horror.

But at the moment, it's all we have.

The full thread in the ubuntu-desktop list discussion referenced in the OP seems to reflect a similar range of sentiments as we see here, which is encouraging in that the discussion seems to be evolving towards limiting access to it and/or focusing on creating alternatives that are truly better and at least as complete rather than just exiling it:

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/thread.html#3597](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/thread.html#3597)

---

### Post by ventrical on 2012-01-26
> **rg4w said:**
> Same here.  I can imagine how careless use or unusual systems can cause CCSM to go awry, but here I've played with it long and hard and I've only managed to get one freeze, which occurred while connected to a projector so it's uncertain if the source of the problem was CCSM or my NVidia driver.   In all other cases CCSM has held up like a champ for me - provided I pay attention to the conflict warnings and act appropriately.  In that regard, it's no worse than having Terminal available.

For myself, it's the *result* I get with CCSM that get people's attention; CCSM itself is an ugly way to get those results, not something I would recommend for newcomers once the Unity plugin options find their way into System Settings.

But until something else exists which offers the same degree of control over as many relevant options, I see no harm in leaving it available from apt-get where those who want it will know how to get it.

The advent of Unity has changed many Compiz settings beyond the scope of Unity's UI elements themselves.   For example, in 11.10 we have the new auto-maximize behavior which may be beneficial to some, but has been a source of annoyance among many Ubuntu fans I've met.  If Canonical's rigorous usability testing showed that the defaults for this behavior are optimal for a majority of their audience I can't find fault with those defaults, but it would be at best risky to assume that those defaults are best for everyone.   CCSM allows the user to change that, but I haven't yet seen anything else which does.

Most of the many comments in this forum and across the web criticizing Unity have done so not in wholesale rejection of the goals Unity seeks to address, but with the details of how it seeks to meet those goals.  Providing a way for the user to adjust the details to their liking would eliminate most complaints about it.

CCSM isn't the answer for that for many reasons, not the least of which is a UI that makes people scream in horror.

But at the moment, it's all we have.

The full thread in the ubuntu-desktop list discussion referenced in the OP seems to reflect a similar range of sentiments as we see here, which is encouraging in that the discussion seems to be evolving towards limiting access to it and/or focusing on creating alternatives that are truly better and at least as complete rather than just exiling it:

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/thread.html#3597](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/thread.html#3597)



Masterfully put. I think this sums it up bang on. But navigating through the ccsm UI hasn't been that much of a difficulty, really, at least for me. It many cases  it walks through itself and has several 'anti-bust' capabilities .. but I think , also, that a new user may feel enthusiastically challenged whether or not they bust their desktop or not. But  then again . I do not speak for all users.  Still , then my point being is that one does not have to be an extraordinary super user to learn to navigate ccsm.

---

### Post by rg4w on 2012-01-26
> **ventrical said:**
> "we want to deliver something to the audience that really rocks their world"

Mark Shuttleworth

[http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related](http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related)
Great find - thanks for that.

Here's another encouraging sign:

The top eight job postings on this list for Canonical are all related to user interface design:
[https://tbe.taleo.net/NA3/ats/careers/searchResults.jsp?org=CANONICAL&cws=1&act=sort&sortColumn=2&sortColumn=0](https://tbe.taleo.net/NA3/ats/careers/searchResults.jsp?org=CANONICAL&cws=1&act=sort&sortColumn=2&sortColumn=0)

Some of those position titles bode especially well, including Head of Design, Usability Specialist, and User Experience Architect.

But the job description for that last one is especially interesting, as it includes:

> Lead and manage the creation of a set of Human Interface Guidelines (HIG) for Ubuntu[https://tbe.taleo.net/NA3/ats/careers/requisition.jsp;jsessionid=EEB2E8CC81167C20EB4C145225E3AA79.NA3_primary_jvm?org=CANONICAL&cws=1&rid=366](https://tbe.taleo.net/NA3/ats/careers/requisition.jsp;jsessionid=EEB2E8CC81167C20EB4C145225E3AA79.NA3_primary_jvm?org=CANONICAL&cws=1&rid=366)

That's big.  Every great OS needs a HIG, and Ubunty has long outgrown the applicability of the Gnome HIG.

Looking at those job postings, I can't wait to see what will show up in 12.10 and 13.04....

---

### Post by fjgaude on 2012-01-26
> **ventrical said:**
> "we want to deliver something to the audience that really rocks their world"

Mark Shuttleworth

[http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related](http://www.youtube.com/watch?v=IxffVEHNyYs&feature=related)

Rock on...

Yeah, it's gonna be a long two years! And all I wished for was a fast tool, an OS, that permitted me to do my work in less time.

---

### Post by ventrical on 2012-01-26
> **rg4w said:**
> Great find - thanks for that.

Here's another encouraging sign:

The top eight job postings on this list for Canonical are all related to user interface design:
[https://tbe.taleo.net/NA3/ats/careers/searchResults.jsp?org=CANONICAL&cws=1&act=sort&sortColumn=2&sortColumn=0](https://tbe.taleo.net/NA3/ats/careers/searchResults.jsp?org=CANONICAL&cws=1&act=sort&sortColumn=2&sortColumn=0)

Some of those position titles bode especially well, including Head of Design, Usability Specialist, and User Experience Architect.

But the job description for that last one is especially interesting, as it includes:

[https://tbe.taleo.net/NA3/ats/careers/requisition.jsp;jsessionid=EEB2E8CC81167C20EB4C145225E3AA79.NA3_primary_jvm?org=CANONICAL&cws=1&rid=366](https://tbe.taleo.net/NA3/ats/careers/requisition.jsp;jsessionid=EEB2E8CC81167C20EB4C145225E3AA79.NA3_primary_jvm?org=CANONICAL&cws=1&rid=366)

That's big.  Every great OS needs a HIG, and Ubunty has long outgrown the applicability of the Gnome HIG.

Looking at those job postings, I can't wait to see what will show up in 12.10 and 13.04....

  But I can sort of see a writing on the wall. and I think Canonical intends to  diversify cross-platforming and be able to have traditional Windows and Mac user cross the isle. So binding compiz or ccsm or  a similar app with the same capabilities would be the  best way to reach out to a more conservative set of end_users. This is where a HIG would bear fruit, but , there may be a backlash , a rebellion of sorts, of the more traditional users who tend to be more independent and open concept minded. It would be , (I can't do this  or I can't do that.. shall I go elsewhere?). Nevertheless, I can understand that Ubuntu has to progress onwards to be more buisness oriented.

  One thing for certain is that there are always refreshing surprises under the Ubuntu wrappers :)

---

### Post by mc4man on 2012-01-26
from link - 
> - It's possible to accidentally uncheck the Unity plugin, breaking the
user's desktop.
Really - can't quite see how to do that

> - It has a load of checkboxes for plugins that we don't support,
allowing infinite combinations of untested options, which result in
either a broken desktop or a misconfigured one

Care to actually name them, in any event if a plugin is truly unsupported & libable to cause a broken desktop then remove the plugin from it's package, ccsm only shows what plugins are installed

> - Since it's settings are separate from Unity a "unity --reset"
doesn't fix it, you have to blow away .compiz or some other dotfile
directories to get a desktop back.
Untrue & atm you'd be hard pressed to 'lose your desktop' , less so if any 'bad' plugins are removed

->  Alex Chiang has documented some of the issues he's run into here:
Outdated  & uninformed when it wasn't so.

> - I'm sure at UDS you've seen didrocks show you one of the ways it
breaks even when using parts of it that shouldn't break.

Likely true but wasn't there, care to enlighten on what & how?
> 
MyUnity is a better user-facing tool anyway for those that want to
play,

You've got to be kidding..

> it would be a shame to have the ccsm tool ship in an LTS.
It doesn't ship, & the tool itself isn't that big an issue, only some possible uses of combined with some users.

The biggest bug with ccsm atm in 12.04 is this bug & even then it not too big a deal
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/833326](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/833326)

Edit: if proposing to dump ccsm then what about "compiz-plugins" & "compiz-plugins-main"? (which are in Main, so if there are issues with some of the included plugins then fix or remove the problem ones

---

### Post by ventrical on 2012-01-26
> **fjgaude said:**
> Yeah, it's gonna be a long two years! And all I wished for was a fast tool, an OS, that permitted me to do my work in less time.


 I still have Lucid in my back pocket. :)

---

### Post by fjgaude on 2012-01-26
> **ventrical said:**
> I still have Lucid in my back pocket. :)

So far, 11.10 and 12.04 is faster for what I do than anything I've tried. But I'm biased, as I stay with WinAP VM and never use a Mac. I do like what I've tried on some tablets, like Android ones. Google did it, so can Shuttleworth.

---

### Post by jbicha on 2012-01-26
> **castrojo said:**
> EDIT: Doesn't the fallback session use metacity?

You can use Ubuntu Classic--which uses Compiz--or use Ubuntu Classic (No Effects)--which uses Metacity.

---

### Post by MacUntu on 2012-01-26
How's CCSM broken if all issues started with adding the unityshell plugin? 

[LIST]
[*]Make Unity configurable outside of CCSM (already ongoing),
[*]Don't allow the deactivation of the unityshell plugin when using the 'ubuntu' Compiz profile,
[*]Hide the unityshell plugin in CCSM,
[*]Leave CCSM alone!
[/LIST]

Side note: People playing around with CCSM is the consequence of not offering a way to easily configure Unity in the first place. It's no like users haven't asked for something like that from the beginning.

---

### Post by castrojo on 2012-01-27
> **MacUntu said:**
> People playing around with CCSM is the consequence of not offering a way to easily configure Unity in the first place. It's no like users haven't asked for something like that from the beginning.

Indeed, and we're now finally getting tools that can replace it that don't suck, so why keep around a buggy tool?

---

### Post by mc4man on 2012-01-27
> **castrojo said:**
> Indeed, and we're now finally getting tools that can replace it that don't suck, so why keep around a buggy tool?

Does "it" extend beyond unity?
That mailing list contains a lot of claims to issues due to "cssm", not sure that the bulk of it is based on current fact or really from ccsm instead of plugins provided by Ubuntu

---

### Post by kansasnoob on 2012-01-27
> **jbicha said:**
> You can use Ubuntu Classic--which uses Compiz--or use Ubuntu Classic (No Effects)--which uses Metacity.

+1! However some tweaking was needed to get Compiz to run in classic, but that's OT here ;)

---

### Post by kansasnoob on 2012-01-27
> **EgoGratis said:**
> Won't Compiz replace Metacity in the future? Wasn't it replaced with Mutter in Gnome 3? Will Compiz be used in the future releases or it will be replaced and with what if it will be?

Really OT here, but the fallback session in gnome3 still uses Metacity. In Ubuntu one has the choice of "classic" which uses (or should use) Compiz, or "classic (no-effects)" which uses Metacity.

And AFAIK Unity-2D also uses Metacity.

I was only trying to point out that my personal preference for Metacity makes me an unreliable source of info regarding Compiz. But w/o CCSM how would one apply some of the most often requested tweaks like the cube, or wobbly windows, etc?

---

### Post by pajn on 2012-01-27
> **castrojo said:**
> CCSM isn't simple!



Because it breaks people's computers. We don't think or guess that it breaks people's computers, we know it does.

Comnpared to gconf-tool it is, compared to editing files manually it is, compared to compiling you own compiz with different default setttings it is.

We have NO other way configuring compiz (not unity) settings!

It doesn't breaks people's computers, the user does.

Installing fglrx breaks most people's computers.
Removing libc6 breaks people's computers.
Deleting important files breaks people's computers.

All of witch can be done with packages included on the CD. If you are fooling around with advanced tools without knowing how to use them you will probably break something.
We can't remove apt-get, we can't remove rm and we can't remove dd as they are important. The same goes for CCSM.

DD isn't simple, but compared to a small magnet and a steady hand it is. You have to have perspective.

---

### Post by MacUntu on 2012-01-27
> **castrojo said:**
> so why keep around a buggy tool?
Because CCSM isn't buggy for the most part. There's only a small subset of plugins that causes problems, but there's a lot more than that in CCSM.

How are users supposed to configure all the other stuff if CCSM were removed? They could fire up the GConf editor and fiddle around with those settings, but other than CCSM, GConf editor does not handle conflicts at all &#8594; more breakage.

---

### Post by effenberg0x0 on 2012-01-27
I might be completely wrong, but I always thought of CCSM as just an interface that uses a gconf API. 
And I also thought that was partially broken in it was the load/write settings backend. And some outdated/unmaintained plugins. 

For people that are familiar with CCSM code: Does problems really extend beyond that?

Regards,
Effenberg

**EDIT**
PS: It would be nice if we had a list of ccsm bugs considered by developers, so that we could test whether they really exist and affect users.

---

### Post by alphacrucis2 on 2012-01-27
How do I get the cube and the burn without CCSM?

---

### Post by ventrical on 2012-01-27
> **MacUntu said:**
> Because CCSM isn't buggy for the most part. There's only a small subset of plugins that causes problems, but there's a lot more than that in CCSM.

How are users supposed to configure all the other stuff if CCSM were removed? They could fire up the GConf editor and fiddle around with those settings, but other than CCSM, GConf editor does not handle conflicts at all &#8594; more breakage.


  I have been working multiple installs/users with ccsm and different configs thereof. I have found that  with Precise (as well as alpha Ocelot) that there is a certain order or sequence of plugins that have to be followed which will not bust the system. On ealrier systems , such as Lucid for example, this is not the case.

  Now I did install "myunity" and it completely prevented any compiz plugins from being enabled and busted one user so far. Even after uninstalling "myunity" I could not bring that user back up. I am not fretting over this as it was just a crash test dumb terminal anyways.

  So .. it's simple .. looking back on ealrier versions of Ubuntu and how well ccsm worked there and then  comparing with the newer releases (Precise, Ocelot) there has been a dramatic change in how compiz and ccsm work with Unity Desktop Environment.  It does not take a rocket scientist to figure out that  the intergration of the Unity DE has all but FUBARed compiz and ccsm.

  I keep hearing "lets be realistic here .. lets be realiststic...!" .. well.. yes then .. lets be realistic. Simply put, Unity is a badly written patchwork that does , perhaps unintentionally,  obsolete CCSM.

  If this game is about precision then lets be then just that , precise, and point to the culprit (unity) and  not the catalyst (compiz).

  And the "myunity" mini tweak tool is just more lame patchwork to cover pre-existing  faults and weakness in the whole Unity write up. So the honesty and reality here is that Unity , in and of itself, precisely fails to intergrate dynamically with more established services and processes that have been proven and tried.

---

### Post by ventrical on 2012-01-27
> **effenberg0x0 said:**
> I might be completely wrong, but I always thought of CCSM as just an interface that uses a gconf API. 
And I also thought that was partially broken in it was the load/write settings backend. And some outdated/unmaintained plugins. 

For people that are familiar with CCSM code: Does problems really extend beyond that?

Regards,
Effenberg

**EDIT**
PS: It would be nice if we had a list of ccsm bugs considered by developers, so that we could test whether they really exist and affect users.


  I know that this does not adress your original question , but, so far, on my terminals I have found  that if I set the number of desktops in General settings to 4H, 4V and then  Desktop Cube, Rotate Cube, then all the rest seems to fall into place. If I fail to set the number of desktops <FIRST> and  tick off <Rotate Cube> before <Desktop Cube> then I have had a few installs that will break straight away .

  Hope that helps somebody.

However .. with natty/unity3D in Edubuntu it works just as well as with Lucid or Maveric and it doesn't matter which order I set up the plug-ins.


 And then there is always Kubuntu :):)

---

### Post by kansasnoob on 2012-01-27
I was just curious this AM so I booted a KNOPPIX live DVD that I'd used to check some LXDE stuff during the Oneiric dev cycle. It's sort of an oddity for those not familiar with it ;)

It's an un-installable live Debian based distro with LXDE, but evidently using Compiz rather than openbox, since CCSM is implemented out-of-box. 

Anyway, I played with CCSM in KNOPPIX-V6.7.0-DVD (2011-08-01) and it doesn't seem buggy at all. I didn't think to check the version but that would be easy to check because it boots in about one minute.

So I wonder, if in fact CCSM is only buggy with Unity, or with certain Unity plugins, maybe only the Unity plugins should be axed in favor of MyUnity :confused:

I also wonder, and my mind wanders too, what if we did a better job of providing a method to revert to out-of-box defaults? I've personally found that just blowing away (or renaming) .compiz-1, .gconf, .config, and .gnome2 and either rebooting or restarting X usually brings me back to default settings.

Just thinking out loud here, but regardless I'm certainly glad Jeremy brought this up :D

Personally when I use either Unity or Unity-2D the only things I change are what's available in the Launcher, and adding these three goodies:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

[https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors)

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

Well, and sometimes I axe the overlay-scrollbars, but I'm trying to adapt to that.

---

### Post by TerryNewton on 2012-01-27
Keep CCSM. Sure the user needs to be careful using it but the same is true for thousands of other tools that aren't installed by default (and many that are). For Unity, so far the new config tools don't address many of the options available in CCSM, but the bigger issue is that it is needed to set up environments that have nothing to do with Unity. For example on my Precise test setup the Gnome Classic with effects session was loading the Unity plugin so I used it to create another compiz configuration without the plugin. Maybe that was fixed by an update, but even if it was I still would want access to it to create new configurations (that don't use Unity). Sure [g|d]conf-editor can access the settings but that would be a buggy badly-discoverable mess, and if a user screws up their system using CCSM it's not that hard to recover... correct me if I'm wrong but isn't it just deleting the .compiz-1 from the home directory after booting to recovery or from a live CD?

If the Ubuntu devs really don't want it to be used with Unity then there are other ways to solve that than removing it altogether... a drastic one would be to add it to the conflicts for the unity package but that would be lots better than removing. A better option would be to simply put up a big fat warning dialog with a cancel if CCSM is run while Unity 3D is running. Taking it away from everyone just because the developers of one plugin doesn't want that plugin to be configured using it just seems like an unreasonable solution, and the only real bug I've heard mentioned (the scroll thing) is apparently easily fixable (but I've never had an issue with that).

---

### Post by mc4man on 2012-01-27
It certainly looks like the tenor of the discussion on ubuntu-desktops mailing list is leaning towards removal - I'd think this is about the gist of it

> Right, the not-so-technical users following forum posts from the internet are the ones who got screwed and the ones we should care most about, users who are technical enough to deal with the side effects of ccsm are also probably technical enough to go through some extra steps to get it installed 

What's somewhat interesting here is that the 2 major reasons for a broken desktop -
 
The bug in python-compizconfig that caused users clicking on Preferences to to switched to the "Default" profile, (no unity) That issue was known in 11.10 dev, *early Oct.,  but not fixed until well after 11.10 release, *late Nov.

While there was some poor advice given in various places, whose really at fault here?

The 2nd continuing issue is concerning enabling rotate/cube which always disables unity. This goes way back to natty dev [where it was decided to make unity depend on Wall]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") (later changed to LargeDesktop to allow cube/rotate

This reason for doing that was to 'Protect' users from running unity without either wall or rotate enabled. The irony is the fix has caused more user issues than would have been if it was never applied. 

Really quite unbelievable but not atypical of how decisions are currently made.

---

### Post by ventrical on 2012-01-27
> **kansasnoob said:**
> I was just curious this AM so I booted a KNOPPIX live DVD that I'd used to check some LXDE stuff during the Oneiric dev cycle. It's sort of an oddity for those not familiar with it ;)

It's an un-installable live Debian based distro with LXDE, but evidently using Compiz rather than openbox, since CCSM is implemented out-of-box. 

Anyway, I played with CCSM in KNOPPIX-V6.7.0-DVD (2011-08-01) and it doesn't seem buggy at all. I didn't think to check the version but that would be easy to check because it boots in about one minute.

So I wonder, if in fact CCSM is only buggy with Unity, or with certain Unity plugins, maybe only the Unity plugins should be axed in favor of MyUnity :confused:

I also wonder, and my mind wanders too, what if we did a better job of providing a method to revert to out-of-box defaults? I've personally found that just blowing away (or renaming) .compiz-1, .gconf, .config, and .gnome2 and either rebooting or restarting X usually brings me back to default settings.

Just thinking out loud here, but regardless I'm certainly glad Jeremy brought this up :D

Personally when I use either Unity or Unity-2D the only things I change are what's available in the Launcher, and adding these three goodies:

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

[https://launchpad.net/~alexmurray/+archive/indicator-sensors]("https://launchpad.net/%7Ealexmurray/+archive/indicator-sensors")

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

Well, and sometimes I axe the overlay-scrollbars, but I'm trying to adapt to that.

 Knoppix is great in many cases. I even had compiz and fusion running on a 333MHz Asus Laptop with only 256MB of SDRAM (and had the cube working there) !

  Perhaps some of the unhappy ones with compiz  and ccsm are running bloated hybrid hardware systems that cannot hyperthread with the traffic cops in Unity, ccsm and other depends. This will definitely be the result if you have a hurry_up_processor being overclocked -and that then is a bogus result..but some results show that ccsm as a whole is (or was) attempting to compensate for those scenarios.

---

### Post by EgoGratis on 2012-01-27
> Right, the not-so-technical users following forum posts from the  internet are the ones who got screwed and the ones we should care most  about, users who are technical enough to deal with the side effects of  ccsm are also probably technical enough to go through some extra steps  to get it installed

And these same users will now copy/paste terminal commands found on forum posts from the internet. "Ultimate guide to setup Compiz with command line".

---

### Post by EgoGratis on 2012-01-27
Why was such feature rich compositor choosed for Ubuntu in the first place if user should only be able to setup one plugin for it?

If this is the scope for compositor in Ubuntu then i would like to see not only CCSM but everything else that will not be used by Ubuntu to be removed as it will not be used and it will be useless for the user and i do agree forcing users to use command line for setup is useless for majority of users that i do imagine will do just that based on some forum posts from the internet.

---

### Post by kansasnoob on 2012-01-27
> **ventrical said:**
> Knoppix is great in many cases. I even had compiz and fusion running on a 333MHz Asus Laptop with only 256MB of SDRAM (and had the cube working there) !

  Perhaps some of the unhappy ones with compiz  and ccsm are running bloated hybrid hardware systems that cannot hyperthread with the traffic cops in Unity, ccsm and other depends. This will definitely be the result if you have a hurry_up_processor being overclocked -and that then is a bogus result..but some results show that ccsm as a whole is (or was) attempting to compensate for those scenarios.

Lets not get too far off track here. I typically use Metacity due to poor visual acuity, not bad enough yet to depend on Universal Access tools, but I don't care for anything "flashy". Even with Gnome version 2.* I always selected "no effects" because it's more suitable for me, and many other seniors.

I only tried CCSM with that KNOPPIX DVD because I recalled that it had some effects working out-of-the-box. I'm actually kind of surprised that Compiz can work so well with LXDE, which I'd think indicates that it could also work well with XFCE :o

The question that presents itself to me is just how does Ubuntu/Canonical plan to address the ability to customize Unity. As far back as Notify-OSD SABDFL indicated the desire to limit any tweaks, and I can now see the reasoning behind that.

I can now boot an Ubuntu live CD, or install Ubuntu, and regardless of whether it's 2D or 3D, depending on hardware capabilities, I get the same thing every time. While it's fair to argue whether or not that's good, it's also fair to argue that getting the same, or at least quite similar, results each time is desirable.

Certainly similarity between devices is preferable, and for those of us that prefer something truly "classic" several options still exist. **This is where I get back on-topic!**

If we remove CCSM from the repos who is going to maintain a PPA? Those who want CCSM are going to want something that's not outdated, but they'll also not want something buggy :D

If it's not in the repos we're likely to find end users downloading .debs from the Debian package lists to "build their own" which seems kind of scary to me :(

Once again I'm glad that Jeremy brought this up. It is a big deal.

---

### Post by ventrical on 2012-01-27
At this stage of the game I am not sure where you are all getting your information because as I had posted in a new thread <someone> has completely repaired the 'preference' option that deals with (import) (export) of compiz profile files. So when I am importing a file there is  only  one reset, flicker and then all the settings are loaded and workable without a reboot. This was not the state it was in the last time I worked on that option ... so somebody is caring for it.

  My eyesight is not the best either. One of the main reasons I admire and use compiz and ccsm. We have been through this discussion before in other threads and I was part of the experimental beta testing during the beta Ocelot.

  I highly doubt that compiz or ccsm will be ejected  or dissed from the repos.  Appears there is just some disinformation campaign going on.

---

### Post by ventrical on 2012-01-27
The busted wayland-demos are in the repos now if anyone is brave enough to try them :)
Whoops,, they are busted and will. not download.

---

### Post by ventrical on 2012-01-27
"
Really, making claims that now because I'm employed by Canonical that  the X11 backend will receive no love or even that I want to "rewrite"  compiz for wayland seems a bit far-fetched to me.

X11 is still a crucial part of how we work and I wouldn't expect  support (or even regular development) for that to be dropped any time  soon (and by soon I mean within the next 4 years). What I was merely  trying to say in my blog post was "let's at least try the waters and see  how they feel"


<Sam Spillsbury>


  Perhaps in 4 years .. yes .. wayland and a compiz rewrite and repo diss of ccsm may be a real possibility.

---

### Post by ventrical on 2012-01-27
and just checked out launchpad and it seems that Sam is red hot working on compiz ...

---

### Post by mc4man on 2012-01-27
thought it would be interesting to show the beginnings of the g-c-c unity pref's.
Obviously it is only a start but what does stand out is 2 things in the behavior section

1st the  hide mode of the launcher has been truncated to 2 choices, dodge & never. Dodge active window  & auto-hide aren't available (whether this reflects what options are to be avail. down the road don't know

2nd, the reveal mode allows 2 choices, the default left edge or top left corner, though top left corner is really 'top left corner, pull cursor down left side'. 
What's notable there is the setting in the screen isn't possible from the dialog box, (disable reveal altogether), that can only be done from ccsm or gconf

Edit: there is some on purpose mis-information above, only to point out how unity settings ccsm are clear, so far in g-c-c not quite so

---

### Post by kansasnoob on 2012-01-27
@ ventrical, I hope I didn't make you mad. I was simply trying to clarify my thoughts.

I do think that dumping CCSM from the repos altogether is NOT a good idea. Doing so will only result in others trying to bring it back via PPA or dot_debs.

Smile and enjoy the deer in my yard:

[http://ubuntuforums.org/showthread.php?p=11645526#post11645526](http://ubuntuforums.org/showthread.php?p=11645526#post11645526)

How awesome is that?

---

### Post by BlinkinCat on 2012-01-27
> **kansasnoob said:**
> 

Smile and enjoy the deer in my yard:

[http://ubuntuforums.org/showthread.php?p=11645526#post11645526](http://ubuntuforums.org/showthread.php?p=11645526#post11645526)

How awesome is that?

Looks cool, would even be better with a beer - :)

---

### Post by kansasnoob on 2012-01-27
> **BlinkinCat said:**
> Looks cool, would even be better with a beer - :)

I was just pouring my first double-shot of bourbon :)

I never seem to have my camera handy when they're out like that, but this time I did :)

Sorry to go so OT, I promise I'll be good now.

---

### Post by ventrical on 2012-01-27
> **mc4man said:**
> thought it would be interesting to show the beginnings of the g-c-c unity pref's.
Obviously it is only a start but what does stand out is 2 things in the behavior section

1st the  hide mode of the launcher has been truncated to 2 choices, dodge & never. Dodge active window  & auto-hide aren't available (whether this reflects what options are to be avail. down the road don't know

2nd, the reveal mode allows 2 choices, the default left edge or top left corner, though top left corner is really 'top left corner, pull cursor down left side'. 
What's notable there is the setting in the screen isn't possible from the dialog box, (disable reveal altogether), that can only be done from ccsm or gconf

Edit: there is some on purpose mis-information above, only to point out how unity settings ccsm are clear, so far in g-c-c not quite so


Thanks for that mac4man. However, I still think that the Unity devs are obsfucating the core issue of bad programming. It's counter productive. It's like what Microsoft did to Outlook Express, by replacing it with a more virus receptive Windows Live Mail... and they left all those legacy users  hanging out to dry and expected them to adapt on their own time ... not the down_time created by Microsoft. And so now with this myUnity (you deserve a break today) concept we have here a plethora of parsing that will have to be done and how can Precise realistically produce a stable LTS by that deadline in light of all this floss and dazzle?

---

### Post by ventrical on 2012-01-27
> **kansasnoob said:**
> @ ventrical, I hope I didn't make you mad. I was simply trying to clarify my thoughts.

I do think that dumping CCSM from the repos altogether is NOT a good idea. Doing so will only result in others trying to bring it back via PPA or dot_debs.

Smile and enjoy the deer in my yard:

[http://ubuntuforums.org/showthread.php?p=11645526#post11645526](http://ubuntuforums.org/showthread.php?p=11645526#post11645526)

How awesome is that?

 No .. I am not mad kansasnoob.  Thank you for your thoughts respectfully so. I am emphatic about ccsm and I feel my enthusiasm is not misplaced. In fact , I am doing the same which you are - just trying to clear my thoughts.

  The OP made a grab from another link and  put the question to us .. and so we are getting some good responses - pro and con. But I think that this whole issue about removing ccsm from the repos is ludicrous in contradistinction to  the "our goal, our mission .. 200million users' clarion call of our captain and  commander, Mark Shuttleworth. And he detailed that this was his goal by the time of the release  date of Precise. There is just no way that this will happen.  So basically I just disagree, cordially with the original link script from Jorge.  CCSM is part of the Linux and Ubuntu family. To remove CCSM from the repos is Un-Ubuntu!!

---

### Post by cariboo on 2012-01-27
@ventrical, just a slight correction, that was 200 million users in 4 years from UDS-P.

---

### Post by ventrical on 2012-01-27
> **cariboo907 said:**
> @ventrical, just a slight correction, that was 200 million users in 4 years from UDS-P.

 I'll throttle down the rockets then ... :)

---

### Post by tomski on 2012-01-28
i don't think ccsm should be removed but instead i think the following:

remove unity (fork it along with compiz or make it a separate app rather than compiz plugin)

fix ccsm bugs

if you just remove it purely on the notion that 'it causes issue's with unity' then erm I am afraid you have forgotten the following:

1) flexibility of Linux based distributions
2) other users whom may not use unity but use compiz


Also to add to this ALL ubuntu documentation needs to be edited to include alternatives to ccsm which can be used when following ubuntu howto's and others.

The points i raised here should be the focus of this venture & not just the direct removal of said app, yes it has bugs & yes it can cause damage easily but many apps in the repo's have bugs & lot's of them can also 'do damage'

---

### Post by lucazade on 2012-01-28
> **tomski said:**
> i don't think ccsm should be removed but instead i think the following:

remove unity (fork it along with compiz or make it a separate app rather than compiz plugin)

fix ccsm bugs

if you just remove it purely on the notion that 'it causes issue's with unity' then erm I am afraid you have forgotten the following:

1) flexibility of Linux based distributions
2) other users whom may not use unity but use compiz


Also to add to this ALL ubuntu documentation needs to be edited to include alternatives to ccsm which can be used when following ubuntu howto's and others.

The points i raised here should be the focus of this venture & not just the direct removal of said app, yes it has bugs & yes it can cause damage easily but many apps in the repo's have bugs & lot's of them can also 'do damage'

it should be removed not only because it causes a lot of issues with unity (that should/ could be fixed) but because is not a human tool to configure a window manager.

it is a jungle of myriads of exotic options, difficult to navigate and to remember.

what we need are good default settings and some simple options inside the gnome control center, inside the appereance applet.

---

### Post by VMC on 2012-01-28
Something new to me is the ability to resize the icons  from the User Interface. It's probably been there from the beginning,  but I always in the past had to install CCSM just for that one item. Now  I don't need CCSM anymore.

---

### Post by ventrical on 2012-01-28
> **lucazade said:**
> it should be removed not only because it causes a lot of issues with unity (that should/ could be fixed) but because is not a human tool to configure a window manager.

it is a jungle of myriads of exotic options, difficult to navigate and to remember.

what we need are good default settings and some simple options inside the gnome control center, inside the appereance applet.

They had (have) compiz-simple but the user-base wanted more , and they got  it. As much as I like Unity I am not going to give up CCSM for it.

---

### Post by mc4man on 2012-01-28
> **VMC said:**
> Something new to me is the ability to resize the icons  from the User Interface. It's probably been there from the beginning,  but I always in the past had to install CCSM just for that one item. Now  I don't need CCSM anymore.

That was just added with a g-c-c upgrade, the behavior tab is a bit bugged, so off to a great start..

---

### Post by BwackNinja on 2012-01-29
This is sad.

Unity != Compiz. Compiz is a fully featured plugin-based and fully-customizable compositing window manager. Unity is a single configuration of that.

Users go to CCSM not because they want a desktop that "just works" but because they want more than that. They want a desktop that is theirs. I approve of unity-specific configuration tools if they make configuring unity clearer and decrease any destructive use of CCSM. I do not approve of moving the configuration of what is meant to be a customizable platform into only the packager's hands. I don't approve of having more hoops to jump through to regain that power. I don't approve of people saying that "you can still edit it through gconf/dconf." CCSM should stay in the archive, but perhaps we should add more profiles for compiz by default to represent the most popular minor changes people normally have to make with CCSM. Also, almost by defintion, **no** configuration change is "unrecoverable" from CCSM.

CCSM is a power user tool. MyUnity is not, and will never be a power user tool.

---

### Post by kansasnoob on 2012-01-29
@ Jeremy Bicha, what if we included only the version of CCSM that matches 'gnome-desktop-environment' which is dependent on either stable or testing Debian :confused:

---

### Post by ventrical on 2012-01-29
> **BwackNinja said:**
> This is sad.

Unity != Compiz. Compiz is a fully featured plugin-based and fully-customizable compositing window manager. Unity is a single configuration of that.

Users go to CCSM not because they want a desktop that "just works" but because they want more than that. They want a desktop that is theirs. I approve of unity-specific configuration tools if they make configuring unity clearer and decrease any destructive use of CCSM. I do not approve of moving the configuration of what is meant to be a customizable platform into only the packager's hands. I don't approve of having more hoops to jump through to regain that power. I don't approve of people saying that "you can still edit it through gconf/dconf." CCSM should stay in the archive, but perhaps we should add more profiles for compiz by default to represent the most popular minor changes people normally have to make with CCSM. Also, almost by defintion, **no** configuration change is "unrecoverable" from CCSM.

CCSM is a power user tool. MyUnity is not, and will never be a power user tool.

There is probably about 400,000 old , used PCs and laptops (after circa 2002) that are just sitting in basements and bins, waiting to be re-discovered. About 80% of those are probably CCSM/COMPIZ capable. Between the 2002/2006 saddlepoint. Windows OSes are pretty well usless on those more legacy PCs unless you want to spend MORE money with licences and professional firewalls . Ubuntu and Compiz w CCSM  can bring that older hardware back to life.  I mean .. even M. Shuttleworth said that he didn't care  if a new app or concept broke something .. as long as it was "punchy and beautiful".. and I assume that goes for COMPIZ too. Some of the older hardware is a far cry better than whats coming out of the ovens today.

---

### Post by mc4man on 2012-01-29
> **kansasnoob said:**
> @ Jeremy Bicha, what if we included only the version of CCSM that matches 'gnome-desktop-environment' which is dependent on either stable or testing Debian :confused:

Not sure that would matter.

What's quite interesting here is the disconnect between bashing a tool & what the tool is used 'on', ie. the plugins themselves, & the effect an enabled unity plugin has when adding or removing some plugins, **irregardless of the tool used.**

Also many of the comments against are using a broad brush without any specifics.

So to comment on 2 specific issues that cause(d) a large number of the user problems & the so-called 'breaking their desktop'

There was a bug in python-compizconfig that when clicking on "Preferences" in ccsm caused the profile to immediately be reset to 'Default' where the unity plugin was not enabled.
This obviously lead to a big problem for users & also some poor advice given as how to recover. *The cleanest fix was simply to just edit or delete ~/.config/compiz-1/compizconfig/config, then log out/in

This bug was  known even before the [1st bug report in early Oct]("https://bugs.launchpad.net/compiz-compizconfig-gconf/+bug/874799"). Ubuntu decided to release without fixing this, maybe they figured not many would click on the big fat **Preferences** on the main ccsm page. (wrong there
The bug itself was not fix released into oneiric until late in  Nov., obviously causing many users to get snagged, though obviously   no longer a problem.
 
The other major cause of the 'broken desktop' is caused when users attempt to switch from wall to rotate.

Unity has always shipped with wall enabled & initially there was no dependency at all.
In natty dev MacUntu correctly pointed out that **IF** [a user disabled wall]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") & didn't enable rotate that part of the unity launcher's function would be lost.
A decision was made to protect these users who did so & make wall a dep.
This shut out users wanting rotate/cube so later a LargeDesktop requirement was added to allow either.

So in trying to protect against **a user-initiated action** that would not break the desktop, a situation was created where now it does.
Though any user who does make the switch should be able to see that unity plugin has been disabled, it's right next to wall/rotate/cube in plain view.

As far as enabling/disabling certain other plugins & having the screen/ccsm/compiz 'reset' or ocassionally hang.

That is solely because of the unity plugin itself - to see open ccsm, disable the unity plugin.
Once the screen/ccsm/compiz resets then enable/disable plugins to your hearts content. Nothing bad happens at all unless you where to enable a plugin that possibly shouldn't be there, (names anyone?) or mis-configure something like window rules ect.

A better solution would be remove any truly non-compatible plugins from the plugin packages in Main & if enabling/disabling some remaining ones while the unity plugin is enabled causes a hang, freeze or whatever, so what, users aren't generally as stupid as is presumed & most times a log out/in will fix all anyway.

---

### Post by kansasnoob on 2012-01-29
> **mc4man said:**
> Not sure that would matter.

What's quite interesting here is the disconnect between bashing a tool & what the tool is used 'on', ie. the plugins themselves, & the effect an enabled unity plugin has when adding or removing some plugins, **irregardless of the tool used.**

Also many of the comments against are using a broad brush without any specifics.

So to comment on 2 specific issues that cause(d) a large number of the user problems & the so-called 'breaking their desktop'

There was a bug in python-compizconfig that when clicking on "Preferences" in ccsm caused the profile to immediately be reset to 'Default' where the unity plugin was not enabled.
This obviously lead to a big problem for users & also some poor advice given as how to recover. *The cleanest fix was simply to just edit or delete ~/.config/compiz-1/compizconfig/config, then log out/in

This bug was  known even before the [1st bug report in early Oct]("https://bugs.launchpad.net/compiz-compizconfig-gconf/+bug/874799"). Ubuntu decided to release without fixing this, maybe they figured not many would click on the big fat **Preferences** on the main ccsm page. (wrong there
The bug itself was not fix released into oneiric until late in  Nov., obviously causing many users to get snagged, though obviously   no longer a problem.
 
The other major cause of the 'broken desktop' is caused when users attempt to switch from wall to rotate.

Unity has always shipped with wall enabled & initially there was no dependency at all.
In natty dev MacUntu correctly pointed out that **IF** [a user disabled wall]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") & didn't enable rotate that part of the unity launcher's function would be lost.
A decision was made to protect these users who did so & make wall a dep.
This shut out users wanting rotate/cube so later a LargeDesktop requirement was added to allow either.

So in trying to protect against **a user-initiated action** that would not break the desktop, a situation was created where now it does.
Though any user who does make the switch should be able to see that unity plugin has been disabled, it's right next to wall/rotate/cube in plain view.

As far as enabling/disabling certain other plugins & having the screen/ccsm/compiz 'reset' or ocassionally hang.

That is solely because of the unity plugin itself - to see open ccsm, disable the unity plugin.
Once the screen/ccsm/compiz resets then enable/disable plugins to your hearts content. Nothing bad happens at all unless you where to enable a plugin that possibly shouldn't be there, (names anyone?) or mis-configure something like window rules ect.

A better solution would be remove any truly non-compatible plugins from the plugin packages in Main & if enabling/disabling some remaining ones while the unity plugin is enabled causes a hang, freeze or whatever, so what, users aren't generally as stupid as is presumed & most times a log out/in will fix all anyway.

My thought, as simple minded as is is, was that the Debian flavor of CCSM would not have the Unity plug-ins. I was then in hopes that would eliminate some of the most common breakage.

But I just can't see having no CCSM at all. That would only lead to folks getting it thru other channels, like a PPA of dot_debs :(

---

### Post by mc4man on 2012-01-29
> **kansasnoob said:**
> My thought, as simple minded as is is, was that the Debian flavor of CCSM would not have the Unity plug-ins. I was then in hopes that would eliminate some of the most common breakage.

But I just can't see having no CCSM at all. That would only lead to folks getting it thru other channels, like a PPA of dot_debs :(
ccsm doesn't contain any plugins, it shows just whatever plugins are installed. 
Clearly they are going to enable some very limited means to configure unity outside of ccsm/gconf/dconf, so there is no real reason to shoot the messenger.

(Ever since natty there has been a means to directly open the unity plugin setting in ccsm but Ubuntu choose to Not make obvious. 

alt+f2 > about:config

---

### Post by BwackNinja on 2012-01-29
> **mc4man said:**
> Not sure that would matter.

What's quite interesting here is the disconnect between bashing a tool & what the tool is used 'on', ie. the plugins themselves, & the effect an enabled unity plugin has when adding or removing some plugins, **irregardless of the tool used.**

Also many of the comments against are using a broad brush without any specifics.

So to comment on 2 specific issues that cause(d) a large number of the user problems & the so-called 'breaking their desktop'

There was a bug in python-compizconfig that when clicking on "Preferences" in ccsm caused the profile to immediately be reset to 'Default' where the unity plugin was not enabled.
This obviously lead to a big problem for users & also some poor advice given as how to recover. *The cleanest fix was simply to just edit or delete ~/.config/compiz-1/compizconfig/config, then log out/in

This bug was  known even before the [1st bug report in early Oct]("https://bugs.launchpad.net/compiz-compizconfig-gconf/+bug/874799"). Ubuntu decided to release without fixing this, maybe they figured not many would click on the big fat **Preferences** on the main ccsm page. (wrong there
The bug itself was not fix released into oneiric until late in  Nov., obviously causing many users to get snagged, though obviously   no longer a problem.
 
The other major cause of the 'broken desktop' is caused when users attempt to switch from wall to rotate.

Unity has always shipped with wall enabled & initially there was no dependency at all.
In natty dev MacUntu correctly pointed out that **IF** [a user disabled wall]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/683211") & didn't enable rotate that part of the unity launcher's function would be lost.
A decision was made to protect these users who did so & make wall a dep.
This shut out users wanting rotate/cube so later a LargeDesktop requirement was added to allow either.

So in trying to protect against **a user-initiated action** that would not break the desktop, a situation was created where now it does.
Though any user who does make the switch should be able to see that unity plugin has been disabled, it's right next to wall/rotate/cube in plain view.

As far as enabling/disabling certain other plugins & having the screen/ccsm/compiz 'reset' or ocassionally hang.

That is solely because of the unity plugin itself - to see open ccsm, disable the unity plugin.
Once the screen/ccsm/compiz resets then enable/disable plugins to your hearts content. Nothing bad happens at all unless you where to enable a plugin that possibly shouldn't be there, (names anyone?) or mis-configure something like window rules ect.

A better solution would be remove any truly non-compatible plugins from the plugin packages in Main & if enabling/disabling some remaining ones while the unity plugin is enabled causes a hang, freeze or whatever, so what, users aren't generally as stupid as is presumed & most times a log out/in will fix all anyway.

One of the big things that need to keep in mind is that Unity is where most of these problems even come into play. I'm not even going so far as calling Unity a problem, but rather saying that its the first thing to have dependencies in such a way that it has brought up scenarios where particulary unsavory things might happen. Rather than using this as an opportunity to remove the one comprehensive tool that configures compiz, we should use this as an opportunity to fix that tool and use these situations to better understand this tool's shortcomings.

We talk about the bug with clicking "Preferences" and that is clearly a bug, not a shortcoming of CCSM, and that was fixed.

We talk about loading and unloading plugins causing compiz to hang or crash, and that would indicate more of a problem in the plugin or compiz than the tool enabling and disabling that plugin. Not a bug in CCSM, should be fixed anyway.

We then talk about the dependency issues that having the Unity plugin raises. The various "Provides" should be grouped together in the UI in a way that shows that you choose between them, not check and uncheck willy-nilly.

We should have a "Unity (default settings)" session option to log into so that people can still be encouraged to mess around and even make their session unusable while still being able to go back to a working and supported configuration in a graphical way, outside of their broken session.

Through all this though, I can still understand the push to avoid instead of fix some problems, especially because a tool like CCSM  shows some rather specific options and has been neglected for years.

PS: I'm mostly done porting CCSM from pygtk to pygi.

---

### Post by effenberg0x0 on 2012-01-29
With almost 3.000 votes, 57.8% believe CCSM should NOT be removed from repos. This is technically a tie (I thought this one would be 70% Keep-CCSM / 30% Ban-CCSM). 

[http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/](http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/)

But anyway, it shows that opinions are divided 50/50. It would be wise to put the ban of CCSM on hold for a while and evaluate it better.

---

### Post by VinDSL on 2012-01-29
> **effenberg0x0 said:**
> With almost 3.000 votes, 57.8% believe CCSM should NOT be removed from repos. This is technically a tie (I thought this one would be 70% Keep-CCSM / 30% Ban-CCSM). 

[http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/](http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/)

But anyway, it shows that opinions are divided 50/50. It would be wise to put the ban of CCSM on hold for a while and evaluate it better.
I always get a chuckle out of percentages.

If you lose 50% of your money, you'll have to increase it 100% to get it back to where it was.

At work we have a joke, about wiring in a 240 volt motor. You have a 50/50/90% chance that it will turn the right direction when you're done - 50/50 chance it be right, 90% chance it will be wrong. LoL!

I think open-source software is the same way!

Just saying...

---

### Post by effenberg0x0 on 2012-01-29
> **VinDSL said:**
> I always get a chuckle out of percentages.

If you lose 50% of your money, you'll have to increase it 100% to get it back to where it was.

At work we have a joke, about wiring in a 240 volt motor. You have a 50/50/90% chance that it will turn the right direction when you're done - 50/50 chance it be right, 90% chance it will be wrong. LoL!

I think open-source software is the same way!

Just saying...
Hey Vin :)
I agree... Having worked with survey statistics and probability for some years, I have seen every sort of results getting interpreted in the most bizarre ways. Formally, we couldn't even accept that this sample is a valid set of the population (those are Internet users that access that specific website, who may or may not really use Ubuntu and may or may not have understood the question, with no stratification, age/sex/location distribution, and etc). And the biggest problem with open source is that since we do not know the exact size of the population (active users), we can never assume that a sample size is valid anyway.

But a valid interpretation of such survey is this: The theme is perceived by opinionated Internet users as an important one, so that while many other surveys get less than 100 votes, this one received 3.000 votes so far. These users are relevant - their habit of posting opinions online makes them what they call "opinion leaders, trend setters, influencers, etc". So, if we disregard the percentages and look at it only from this safe point of view, a logic interpretation would be that, in light of the potential impact the theme has in the community, it calls for a more profound discussion and a thoroughly though decision.  

But I'm playing devil's advocate here. My personal opinion is that the tool must be replaced by something with a modern / coherent UI, safer for the average-user but that does not limit experienced users options and, most important of all, that is actively maintained. I defend that system settings should have a radiobox to select between basic and advanced settings (like some programs, i.e. VLC, do - I had proposed it and posted screenshots [here]("http://ubuntuforums.org/showthread.php?t=1907305&highlight=basic+advanced+settings")).

Regards,
Effenberg

---

### Post by UltimateCat on 2012-01-29
> **ronacc said:**
> why not FIX it instead ?

I'm with you

---

### Post by UltimateCat on 2012-01-29
I depend on Compiz Fusion for the graphic I have with Ultimate Edition 2.7

I like new things and things that are buggy aren't my cup of tea; so my question is;

 Who is going to build and design something better w/o so much buggy stuff going on?

And when will this new type of replacement be out for all to use?

---

### Post by jbicha on 2012-01-29
> **kansasnoob said:**
> @ Jeremy Bicha, what if we included only the version of CCSM that matches 'gnome-desktop-environment' which is dependent on either stable or testing Debian :confused:

This actually isn't my decision at all, nor is it Jorge's, but it will likely end up being a consensus of the Unity & Desktop Team developers. I do appreciate Jorge bringing it up as we all want Ubuntu to be the best quality operating system for the widest number of people. I just posted the mailing-list discussion because I correctly assumed a lot of people would like to know the change was being considered, before it was too late to do anything about it.

I don't have a strong opinion on the issue, mostly because I don't ever use CCSM and don't really recommend it because I've read about too many people breaking their Unity (and therefore their computers) with CCSM. I believe we don't need barely maintained software in our repositories and we don't want software that effectively breaks computers. But as CCSM hasn't really been broken in my personal experience, I can't say whether CCSM is bad enough to be removed.

---

### Post by ventrical on 2012-01-30
> **effenberg0x0 said:**
> With almost 3.000 votes, 57.8% believe CCSM should NOT be removed from repos. This is technically a tie (I thought this one would be 70% Keep-CCSM / 30% Ban-CCSM). 

[http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/](http://www.omgubuntu.co.uk/2012/01/should-ccsm-be-purged-from-the-ubuntu-repos/)

But anyway, it shows that opinions are divided 50/50. It would be wise to put the ban of CCSM on hold for a while and evaluate it better.


It is highly likely that some of the BAN CCSM votes are from noobs that misconfigured CCSM or from devs who are trying to pump MyUnity that have never even tried CCSM (or use CCSM like Jeremy says).

 Considering the noob  factor and the dev MyUnity bias factor, we got well more than your 70/30.


 But I am all for further evaluation.

---

### Post by ventrical on 2012-01-30
> **jbicha said:**
> This actually isn't my decision at all, nor is it Jorge's, but it will likely end up being a consensus of the Unity & Desktop Team developers. I do appreciate Jorge bringing it up as we all want Ubuntu to be the best quality operating system for the widest number of people. I just posted the mailing-list discussion because I correctly assumed a lot of people would like to know the change was being considered, before it was too late to do anything about it.

I don't have a strong opinion on the issue, mostly because I don't ever use CCSM and don't really recommend it because I've read about too many people breaking their Unity (and therefore their computers) with CCSM. I believe we don't need barely maintained software in our repositories and we don't want software that effectively breaks computers. But as CCSM hasn't really been broken in my personal experience, I can't say whether CCSM is bad enough to be removed.


  The only thing that concerns me about all of this is that Shuttleworth has clearly pointed out that "Unity is the driving force behind Ubuntu" , not Ubuntu is the driving force behind Unity. Ultimately he will have  strong brokering powers if a decision is to be made.

 Thanks for the heads up !!

---

### Post by lucazade on 2012-01-30
> **ventrical said:**
> It is highly likely that some of the BAN CCSM votes are from noobs that misconfigured CCSM or from devs who are trying to pump MyUnity that have never even tried CCSM (or use CCSM like Jeremy says).

 Considering the noob  factor and the dev MyUnity bias factor, we got well more than your 70/30.


 But I am all for further evaluation.


really?

i would say just the opposite.. noobs want to waste time behind a frivolous tool like ccsm while expert people don't need, and probably don't have time, to spin the cube or customize panel color.

i'm wondering if all this ccsm fan would use linux without compiz.. they are likely sons of youtube-compiz-cube-mania..

---

### Post by ventrical on 2012-01-30
> **lucazade said:**
> really?

i would say just the opposite.. noobs want to waste time behind a frivolous tool like ccsm while expert people don't need, and probably don't have time, to spin the cube or customize panel color.

i'm wondering if all this ccsm fan would use linux without compiz.. they are likely sons of youtube-compiz-cube-mania..

  They are certainly not the sons of a null-space terminal and , basically, without compiz, Ubuntu will loose it's market share.

Remember   ... Ubuntu is for human beings , not robots. Ubuntu loved the marriage to  CCSM in earlier releases for the general masses. Now, because of Unity induced compiz bugs they want to drop it?

 Obviously the MyUnity team would like to spike the spinnaker but Compiz already has a full wind in it's user base.

  Ok.... so  the devs remove CCSM .. and then what do we got ??  A Turing machine. That takes us back 30 years.  This is not a "punchy and beautiful" concept and it certainly does not "rock my world".

---

### Post by lucazade on 2012-01-30
> **ventrical said:**
> They are certainly not the sons of a null-space terminal and , basically, without compiz, Ubuntu will loose it's market share.


LOL.. I don't think Ubuntu success is due to compiz and it could surely survive without it... anyway I respect compiz fans and what I suggest is porting part of ccsm inside the appereance applet of control center.

---

### Post by ventrical on 2012-01-30
> **lucazade said:**
> LOL.. I don't think Ubuntu success is due to compiz and it could surely survive without it... anyway I respect compiz fans and what I suggest is porting part of ccsm inside the appereance applet of control center.

  We don't want Ubuntu to just be a survivor, we want it to be a real winner!!  A lot of the bugs that were with Ocelot are gone now .. even with alpha Precise .. it's work so much better .. but the good thing about Ubuntu as a whole is that there is always work to be done.

---

### Post by kansasnoob on 2012-01-30
> **jbicha said:**
> This actually isn't my decision at all, nor is it Jorge's, but it will likely end up being a consensus of the Unity & Desktop Team developers. I do appreciate Jorge bringing it up as we all want Ubuntu to be the best quality operating system for the widest number of people. I just posted the mailing-list discussion because I correctly assumed a lot of people would like to know the change was being considered, before it was too late to do anything about it.

I don't have a strong opinion on the issue, mostly because I don't ever use CCSM and don't really recommend it because I've read about too many people breaking their Unity (and therefore their computers) with CCSM. I believe we don't need barely maintained software in our repositories and we don't want software that effectively breaks computers. But as CCSM hasn't really been broken in my personal experience, I can't say whether CCSM is bad enough to be removed.

Regardless of the outcome thanks for the info. I'm in the same boat, in so far as not really being effected, because I tend to prefer Metacity via either Unity-2D or Classic (no effects).

You may be aware of my Oneiric Classic (no effects) thread:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

While I didn't want to bother even testing "classic" with Compiz for Oneiric, I had hoped to post something similar for Precise but including steps for both Metacity and Compiz. Without CCSM it might be pointless for me to even pursue the classic + Compiz route because I'm sure I'd be plagued with compiz configuration questions that I'd not be able to answer.

OTOH I really can see Jorge's point. On those computers where I prefer Unity I find the need for minimal customization to be one of it's greatest attributes. If CCSM commonly breaks Unity then that somehow needs to be addressed, I'm just not sure how it should be accomplished :D

BTW I may join that mailing list, as I find a lot of it very interesting. Somewhat more so than Ayatana, but I really have kind of a full plate ATM. I particularly liked this:

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003595.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003595.html)

---

### Post by philinux on 2012-01-30
Well here you go. Another one.

[http://ubuntuforums.org/showthread.php?t=1917605](http://ubuntuforums.org/showthread.php?t=1917605)

I'm happy to see it go as long as I can get it from somewhere either ppa or a .deb.

All I need is desktop zoom and a couple of keyboard shortcuts.

---

### Post by ventrical on 2012-01-30
> **philinux said:**
> Well here you go. Another one.

[http://ubuntuforums.org/showthread.php?t=1917605](http://ubuntuforums.org/showthread.php?t=1917605)



Geesh .. but Phil... a complete noob with only three beans and he didn't even mention what kind of PC he had. And for all we know it could be a dev in cognito :)  I know the Unity guys are under pressure for release date but to try and pin CCSM as the culprit  is not fair.

---

### Post by philinux on 2012-01-30
> **ventrical said:**
> Geesh .. but Phil... a complete noob with only three beans and he didn't even mention what kind of PC he had. And for all we know it could be a dev in cognito :)  I know the Unity guys are under pressure for release date but to try and pin CCSM as the culprit  is not fair.

I know. Lol. But this is not the first I've seen. I've done it too. :P

And it's the noobs they are trying to protect. Then again CCSM is not installed as default so a user has to specifically install it. Whether they know the pitfalls is another thing.

---

### Post by ventrical on 2012-01-30
> **philinux said:**
> I know. Lol. But this is not the first I've seen. I've done it too. :P

And it's the noobs they are trying to protect. Then again CCSM is not installed as default so a user has to specifically install it. Whether they know the pitfalls is another thing.


I am all for  protecting noobs  but  (and I am not pointing at you or anyone)  this is beta testing !! I mean .. even during Ocelot testing Jorge  dropped in with a PPA link to test the new experimental CCSM. I busted a few desktops .. but thats part of the beta testing process.

  I know even already that there had been kernel regression with Precise trying to build a driver for 64bit ATI Radeon 1250. It (unity&compiz/ccsm) worked great with Ocelot but as soon as I installed Precise alpha (twice on the same machine) there was no way that I could get Unity 3D. So compiz cannot be faulted in situations like these .. (and I know there are a ton of those also).

   I guess I can say fairly that if nobody is willing to take up the reigns from Sam Spilsbury or that the COMPIZ project is not seconded to another group then , really, there is no choice but to dump it. I would just think through these testing periods that we give Sam and  even others in the Unity team to come up with something .. or even one of the end_users. and it's just my opinion that myUnity is not the answer.

---

### Post by philinux on 2012-01-30
> **ventrical said:**
> I am all for  protecting noobs  but  (and I am not pointing at you or anyone)  this is beta testing !! I mean .. even during Ocelot testing Jorge  dropped in with a PPA link to test the new experimental CCSM. I busted a few desktops .. but thats part of the beta testing process.

  I know even already that there had been kernel regression with Precise trying to build a driver for 64bit ATI Radeon 1250. It (unity&compiz/ccsm) worked great with Ocelot but as soon as I installed Precise alpha (twice on the same machine) there was no way that I could get Unity 3D. So compiz cannot be faulted in situations like these .. (and I know there are a ton of those also).

   I guess I can say fairly that if nobody is willing to take up the reigns from Sam Spilsbury or that the COMPIZ project is not seconded to another group then , really, there is no choice but to dump it. I would just think through these testing periods that we give Sam and  even others in the Unity team to come up with something .. or even one of the end_users.

I agree. I'm waiting to see what the devs decide.

---

### Post by kansasnoob on 2012-01-30
> **philinux said:**
> Well here you go. Another one.

[http://ubuntuforums.org/showthread.php?t=1917605](http://ubuntuforums.org/showthread.php?t=1917605)

I'm happy to see it go as long as I can get it from somewhere either ppa or a .deb.

All I need is desktop zoom and a couple of keyboard shortcuts.

Ah yes, someone wanting the cube :)

Is there a safe way to get the cube in Unity?

---

### Post by rg4w on 2012-01-30
> **kansasnoob said:**
> Is there a safe way to get the cube in Unity?
For myself and apparently a good many others, we've been able to get the Cube working with the popular recipe of first turning off the Unity plugin, setting up the Cube, then turning Unity back on.  This has only failed for me once, while connected to a projector, and given the circumstances it's unclear whether the problem was with CCSM, Unity, or my NVidia driver.   In more than two dozen other cases of following the same recipe (I get a lot of questions about this so I often revert to default Unity and show how to do it from scratch) it's always worked well for me.

I can't say whether this will work for all possible configs, but it seems to be the most common recipe and I haven't yet met anyone who's able to run Unity 3D who did this and it failed.

And of course, as with any such tweaks, you'll want to remember to turn Unity back on before quitting CCSM.  I rebooted with Unity off once just to see what would happen, and while it wasn't hard to get everything back to working order with "unity --reset" it was initially disturbing to boot into a DE with no DE per se. :)

So it goes.  Users can do far more damage to their systems with equally careless use of Terminal.

Removing CCSM from the Software Center while leaving it available for power users to get via apt-get seems simple and consistent with everyone's goals here.

I have to wonder if the next question will be whether Terminal gets pulled....

---

### Post by ventrical on 2012-01-30
> **kansasnoob said:**
> Ah yes, someone wanting the cube :)

Is there a safe way to get the cube in Unity?


 I already posted that.

 Now , where is it ? 

:)

---

### Post by ventrical on 2012-01-30
> **kansasnoob said:**
> Ah yes, someone wanting the cube :)

Is there a safe way to get the cube in Unity?

Dern if you think I can find my post :)

 But what  I do is first set General Option. Go to that option  and set desktop size H4 and V4.

 Then tic off Desktop Cube. There might be a flicker or reset... wait ... Unity Pugin should still be ticked off .. in not then tic it off and there will be some option windows to resolve .. choose resolve conflicts.

Next tic Rotate Cube.  It should flicker is some cases or reset ... wait .. and then the cube should work.  A lot of options that were not set in Ocelot are now set in Precise. You can experiment from there. 

 You should be able to press down your mouse scroller wheel and move mouse and cube will rotate.. else <Ctrl+Alt+arrow-keyleft/right>

or

 you can try this :
[http://ubuntuforums.org/showthread.php?t=1916127](http://ubuntuforums.org/showthread.php?t=1916127)

edit: But make sure you have compiz plugins extra if you import that file.

---

### Post by mc4man on 2012-01-30
> **kansasnoob said:**
> Ah yes, someone wanting the cube :)

Is there a safe way to get the cube in Unity?
As rg4w & myself previously mentioned, simply 1st disabling the unity plugin, then enabling cube/rotate (which will disable wall), then re-enabling unity is the simplest, safest way.
**(or doing any other enabling/disabling of plugins is better with unity 1st. disabled**

If the unity plugin didn't require LargeDesktop then users could just simply switch with no issue at all, as in screen, unity is enabled with nothing yet set as far as wall or rotate

Myself had always found rotate better than wall for desktop based viewport switching, never did use the cube other than rotate needs something to "rotate"
(for quite a large number rotate is now unusable due to flashing, no sign of being fixed
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

Many people use ccsm as a convenient means to make adjustments that aren't the so called eye candy, sometimes quite the opposite

---

### Post by ventrical on 2012-01-30
> **rg4w said:**
> 

I have to wonder if the next question will be whether Terminal gets pulled....


Putting out an extra distro of Precise would'nt hurt if  Ubuntu is trying to protect noobs from borking their systems. 

Ubuntu-Precise-Noob:Getting started with Precise in a safe and comfortable environment.
(no terminal.no ccsm.no.synaptic etc.)
Ubuntu-Precise-Power:For modders, experimenters, hackers and powerusers.
(the works)

 so both noobs and power users will know the difference and cannot plea ignorance..

<noob> "Oh .. I accidently downloaded Ububtu Precise Power  and borked my system ..."

:)

---

### Post by Arthur_D on 2012-01-30
Just to be clear about this: I am not pointing at any specific user with this post.
But seriously, stop the whining. If you tout yourself as a power-user, you should be perfectly able to do the simple act of adding a PPA in order to get your CCSM fix. Making GUI tools which regularly mess up things a little more difficult to get hold of for newbies can only be a good thing. Meanwhile, lazy "power-users" scream because they might have to add a PPA.

Besides, if you don't like it, don't use it. Go to another distro where they are more catered towards power-users.

---

### Post by kansasnoob on 2012-01-30
Just to clarify what I meant when I asked, "Is there a safe way to get the cube in Unity", I was not asking for a how-to ;)

It was rather rhetorical, but also serious. While I've never cared about the cube and other fancy window decorations it's clear that some users love 'em :D

So how do we make everyone happy? 

Was Compiz a poor choice for Unity?

---

### Post by castrojo on 2012-01-30
> **Arthur_D said:**
> Besides, if you don't like it, don't use it. Go to another distro where they are more catered towards power-users.

Ubuntu has plenty to offer power users, this isn't about power users vs. non power users, it's about having something that works. 

Power users also deserve a tool that does what it says it does in a repeatable manner.

---

### Post by ventrical on 2012-01-30
> **Arthur_D said:**
> Just to be clear about this: I am not pointing at any specific user with this post.
But seriously, stop the whining. If you tout yourself as a power-user, you should be perfectly able to do the simple act of adding a PPA in order to get your CCSM fix. Making GUI tools which regularly mess up things a little more difficult to get hold of for newbies can only be a good thing. Meanwhile, lazy "power-users" scream because they might have to add a PPA.

Besides, if you don't like it, don't use it. Go to another distro where they are more catered towards power-users.

 Yeah .. go for it .. I mean stop your yammering and lets get to it .  Pitter, patter .. lets get at er.  I am certainly not screaming about adding a PPA ... I'm just saying that there a lot of talk and no action .. again .. this is beta testing Precise and one of the apps I beta test is compiz .. so if they are going to dump it .. lets go .. I haven't got time for the silliness.

---

### Post by ventrical on 2012-01-30
> **castrojo said:**
> Ubuntu has plenty to offer power users, this isn't about power users vs. non power users, it's about having something that works. 

Power users also deserve a tool that does what it says it does in a repeatable manner.

  When was the last time you BETA busted your desktop with ccsm ?

---

### Post by Arthur_D on 2012-01-30
I don't want to offend, but to be honest it seems like you're doing most of the talking in this thread... ;)

I applaud you for beta testing Ubuntu, and I hope you'll continue with that.
Personally I've moved to Arch Linux for my main computer (I'm still running Ubuntu on my netbook), and thus I won't have to keep up with whatever Canonical decides on. But this is one of the few cases where I agree on one of their controversial moves... or rather, possible moves. The decision of what Ubuntu should have in their repos are not ours to make anyhow.

I just don't see the fuss when this is practically a non-issue for most users, and would add 5 mins. of adding a PPA providing it for those who wants it.
Not to mention, it might prompt people to fix CCSM which should be a win for everyone.

---

### Post by ventrical on 2012-01-30
> **Arthur_D said:**
> I don't want to offend, but to be honest it seems like you're doing most of the talking in this thread... ;)

I applaud you for beta testing Ubuntu, and I hope you'll continue with that.
Personally I've moved to Arch Linux for my main computer (I'm still running Ubuntu on my netbook), and thus I won't have to keep up with whatever Canonical decides on. But this is one of the few cases where I agree on one of their controversial moves... or rather, possible moves. The decision of what Ubuntu should have in their repos are not ours to make anyhow.

I just don't see the fuss when this is practically a non-issue for most users, and would add 5 mins. of adding a PPA providing it for those who wants it.
Not to mention, it might prompt people to fix CCSM which should be a win for everyone.



I'm not talking .. I'm typing :)   Actually I'm typing loudly. Mabey too loud. Sorry Art ... may the Ubuntu be with you man.

 peace..

---

### Post by VMC on 2012-01-30
> **mc4man said:**
> 

....

Many people use ccsm as a convenient means to make adjustments that _aren't the so called eye candy_, sometimes quite the opposite

That would be me.

---

### Post by Arthur_D on 2012-01-30
> **ventrical said:**
> I'm not talking .. I'm typing :)   Actually I'm typing loudly. Mabey too loud. Sorry Art ... may the Ubuntu be with you man.

 peace..
Haha, you're right. :D
And you have nothing to apologize for. :)

Just got to admit I got a little wound up that everyone on OMG!Ubuntu! etc. got so wound up about what I see as a non-issue. I'm a hypocrite, and I know it. :P

I think I can sympathize with those who wonder where to set the bar of which applications should be purged, and which should be available in the standard repos. The case of CCSM is a little special though, since it's been so hyped in blogs and other places as the way to make your friends look at your computer in amazement. Thus there are many newcomers to Linux and Ubuntu in particular, who may end up trashing their desktops without realizing it could be possible with a GUI tool.

Anyway, I'm being caught up in an argument... I've made my choice, and I should really leave it at that... but a good ol' heated discussion is sometimes too tempting to ignore. :)

---

### Post by ventrical on 2012-01-30
> **VMC said:**
> That would be me.


 And me also..

 There is one feature called 'Wallpaper' and using Lucid I can make several  desktops rotate with a different  wallpaper on each cube. What I use is .png file that I have captured as sort of memory peg cards so if I need a quick recall on an important topic, all I have to do is rotate the cube. Ring switcher and app switcher are other ones that are good for the visually challenged and can be configured to be great educational tools as well.

---

### Post by effenberg0x0 on 2012-01-30
> **castrojo said:**
> Ubuntu has plenty to offer power users, this isn't about power users vs. non power users, it's about having something that works. 
Power users also deserve a tool that does what it says it does in a repeatable manner.

The discussion about targeting technical vs non-technical users in UI design has been around for a while now, throughout the move to Unity, its lack of customisation options, and now CCSM. The classification of users into both groups based on UI preferences is flawed as there's some overlap. In face of the average "Total Beginner"/"General Help" audience, I consider myself to be a power user. Yet, I do like and use Unity and some Compiz features: Ex. The "Place Windows" plugin is really important in my daily use.
 
We know Linux distros are no longer used exclusively by IT people. The goal is to reach the average non-technical users and Ubuntu excels on that. It's all about business and a matter of survival: A distro with the infrastructure of Ubuntu can only exist if its adoption by average users continues to grow. But, at the same time, no distro wants to loose its technical users - the ones that test, develop, support and contribute to it. 

If this scenario doesn't change (and I can't see how it would), the leading distros will **have to** come up with a way to please both users groups. Having separate versions, as was mentioned, would be complicated and unnecessary additional work.

The only way I can see this being done effectively is if the UI is adapted to present options for **both** groups (technical / non-technical). In the case of settings, which are critic and the whole point of recent discussions, wouldn't it be easier to adopt the following defaults:

- A radiobox to select between "Basic Settings" and "Advanced Settings". See [this]("http://ubuntuforums.org/showpost.php?p=11605303&postcount=22") example.
- A button to "Reset to Defaults" (And we recently got one in g-c-c)
- A popup dialog when "Advanced Settings" is selected: "Danger Will Robinson! You're on your own if you proceed". Possibly ask for the user password to confirm, etc.    

If such guideline is adopted by Ubuntu in g-c-c (including Compiz Settings) and potentially spread to other applications (slow change - many of them are just packaged and will not change fast), I think Ubuntu would be once again taking the lead in innovation. Devs can go crazy in Advanced Settings and play it safe in the Basic Settings. 

I know this is practically undoable now and that the design/UI definitions are pretty much closed now, but maybe it's a discussion for future UIs. 

Regards,
Effenberg

---

### Post by mc4man on 2012-01-30
Slightly off the ccsm topic - 
when 1st brought up in natty dev about a config tool for unity this statement was made, still wonder here about whether the 'experiment' is over yet & if not, what unity config's will remain available (the bulk are still under the experimental tab

> Some experimental settings will remain.
We have already seen cases where such settings resulted in additional
bugs, so we will remove experimental settings when the experiment is
over and we have an answer. 

---

### Post by EgoGratis on 2012-01-31
Now when Unity settings will be available in system settings a lot of users will not use CCSM any more. 

Tools like MyUnity and Ubuntu Tweak will be recommended officially and they do have active support and can add Compiz features most users use. The future does not look bad too:

> Not only can Wayland surfaces now be transformed in interesting ways --  either for useful purposes like zooming-in on your desktop or just being  used to show-it off and "desktop bling" -- but Wayland is even properly  handling the input transformations (something that's been a problem in  the X.Org world). 

[http://www.phoronix.com/scan.php?page=news_item&px=MTA1MDc](http://www.phoronix.com/scan.php?page=news_item&px=MTA1MDc)

Something that was hard to achieve and maintain will be more simple to achieve and maintain in the future?

All that being said i think removing CCSM in Ubuntu 12.04 would not protect a whole bunch of users but it would take away a lot of features. I don't know if fixing problems CCSM has in some rare cases is worth the effort. The tool should be there in Ubuntu 12.04 but developers should focus on the "future Compiz". Maybe just some obvious warning -> Disabling Unity plugin will break your display. :)

---

### Post by mc4man on 2012-02-01
There was just a change in the ccsm > unity plugin settings that is actually a good thing, most of the sliders were removed. Whenever one would scroll inside of the settings window they tended to get 'caught' & altered.
So something positive..

---

### Post by BeRoot ReBoot on 2012-02-01
I find even the fact that this discussion is taking place deeply disturbing. Choice and configurability should never be removed from users. Add a few more "CAUTION, STOP UNLESS YOU ACTUALLY KNOW WHAT YOU'RE DOING" dialogs if you must, but just yanking stuff from the repos for no good reason other than it being confusing to people who don't even have the basic idea of what they need is just plain uncalled for.

---

### Post by ventrical on 2012-02-01
> **mc4man said:**
> There was just a change in the ccsm > unity plugin settings that is actually a good thing, most of the sliders were removed. Whenever one would scroll inside of the settings window they tended to get 'caught' & altered.
So something positive..

 Yeah .. they really gutted (pruned) all the sliders. Looks like the devs are listening . I e-mailed Sam a couple of days ago.  It's good to see some maintenance  in this area. Sort of a  heads-up that CCSM is here to stay!1 

Bravo to all those who were pro CCSM in this debate.

 thanks..

---

### Post by effenberg0x0 on 2012-02-01
> **Chauncellor said:**
> I think that basing a UI off of VLC is one of the worst ways you can design your program. As much as I love that program it has been a beacon of terrible, terrible design.

How would I answer to that? 

Yea, and not only the UI. I think Ubuntu as a whole should be based in VLC. Programs should be converted into interactive movies. All interfaces should be VLC-like. Ubuntu itself could be a movie running in VLC. That's obviously my point in the previous post.

:)

Regards,
Effenberg

---

### Post by zika on 2012-02-02
> **effenberg0x0 said:**
> :)

Regards,
EffenbergI like Your avatar [IMG]http://www.emofaces.com/en/emoticons/p/paperclip-emoticon.gif[/IMG]

---

### Post by ronacc on 2012-02-02
My feelings on this are CCSM should not be installed by default but should be available for those who wish to use it and are prepared to deal with problems . Atleast until other tools are available that allow the full power of compiz to be accessed and all options to be configured . Perhaps put a warning in the description that it may cause problems in some systems and with some combo's of options .

---

### Post by kansasnoob on 2012-02-02
Expressing our opinions here do little to no good :)

At this point if we have a suggestion I think it's very important to express it here:

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html)

You can join by clicking the link at the bottom of the page and following the instructions.

---

### Post by ventrical on 2012-02-02
> **kansasnoob said:**
> Expressing our opinions here do little to no good :)

At this point if we have a suggestion I think it's very important to express it here:

[https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2012-January/003597.html)

You can join by clicking the link at the bottom of the page and following the instructions.

 I disagree.. I think it does a lot of good to express our opinions openly here. There is a lot of good brainstorming and some good points can be found in this. It encourages us to be more independent in our concepts rather that constrained in our views. We never really know who just might stop in!!

  And it is all for the betterment of Precise in the long run.  It will be better, faster and will 'rock your world' :) CCSM included.
 :)

---

### Post by rg4w on 2012-02-02
> **ventrical said:**
> I disagree.. I think it does a lot of good to express our opinions openly here. There is a lot of good brainstorming and some good points can be found in this. It encourages us to be more independent in our concepts rather that constrained in our views. We never really know who just might stop in!!

  And it is all for the betterment of Precise in the long run.  It will be better, faster and will 'rock your world' :) CCSM included.
 :)
This seems to come up a lot here.  I can appreciate why there are established channels for discussion of design and implementation details (ubuntu-dev list, Ayatana, etc.), but I also feel there's good value in checking in with these forums as a sort of "temperature reading" of the community.

Sure, the posts here won't reflect the whole of the community, and shouldn't be seen as a replacement for more serious studies of user attitudes and expectations.

But the posts in this forum do make a valuable compliment to more serious studies, a sort of organic ethnography that can help the team better understand how to support and engage the current user base.

After all, as with any product, it's the current audience which will do a lot of the work to gain the larger future audience, but such evangelism will only happen to the degree that they understand and are excited about design initiatives, and to the degree that such initiatives truly add value to their Ubuntu experience.

Very few posts here are completely anti-Unity or anti-HUD or anti-anything else. On the contrary, the often express very specific concerns which in many cases can help refine current design objectives.

---

### Post by ventrical on 2012-02-02
> **rg4w said:**
> This seems to come up a lot here.  I can appreciate why there are established channels for discussion of design and implementation details (ubuntu-dev list, Ayatana, etc.), but I also feel there's good value in checking in with these forums as a sort of "temperature reading" of the community.

Sure, the posts here won't reflect the whole of the community, and shouldn't be seen as a replacement for more serious studies of user attitudes and expectations.

But the posts in this forum do make a valuable compliment to more serious studies, a sort of organic ethnography that can help the team better understand how to support and engage the current user base.

After all, as with any product, it's the current audience which will do a lot of the work to gain the larger future audience, but such evangelism will only happen to the degree that they understand and are excited about design initiatives, and to the degree that such initiatives truly add value to their Ubuntu experience.

Very few posts here are completely anti-Unity or anti-HUD or anti-anything else. On the contrary, the often express very specific concerns which in many cases can help refine current design objectives.


  I hope I am only trying to emulate the Shuttleworth spirit of the whole concept of Unity being the "driving force behind Ubuntu" . I think Mark *is* trying to challenge developers  to reach out and test the waters . It would be an exciting design initiative to unify Unity Desktop with CCSM. I mean , for the most part the, Unity Plug-In is the best facsimile that had been produced but the development of CCSM has not really been taken under the Ubuntu wing as Compiz has. So the Unity/Compiz marriage has been trying to birth a child  called MyUnity while at the same time obsoleting and ejecting  a faithful servant in the form of CCSM.

  This is not necessarily anti-CCSM psychobabble  nor is  the chatter about myUnity reckless machinations  but I think , rather , that it is a tensioner  that tries to balance the reasonable and logical  in a punchy and effervescent way.  And it is this effervescence that helps keep the whole argument , whether it is appropiate or not, viable , intriguing  and honest. Otherwise any other presentation would most likely be  glum and irrelevant.

---

### Post by effenberg0x0 on 2012-02-02
> **zika said:**
> I like Your avatar [IMG]http://www.emofaces.com/en/emoticons/p/paperclip-emoticon.gif[/IMG]

Good to see you're a fellow paper clip enthusiast!
Regards,
Effenberg

---

### Post by zika on 2012-02-02
> **effenberg0x0 said:**
> Good to see you're a fellow paper clip enthusiast!
Regards,
EffenbergYou can never have too much different paper-clips... ;)

---

### Post by philinux on 2012-02-02
[http://iloveubuntu.net/new-ccsm-lands-ubuntu-1204-removing-sliders](http://iloveubuntu.net/new-ccsm-lands-ubuntu-1204-removing-sliders)

---

### Post by ventrical on 2012-02-02
> **philinux said:**
> [http://iloveubuntu.net/new-ccsm-lands-ubuntu-1204-removing-sliders](http://iloveubuntu.net/new-ccsm-lands-ubuntu-1204-removing-sliders)


Bravo ! Here .. Here ..!!


How dare then send a dev troll in here :)

---

### Post by cuby on 2012-02-06
CCSM is not production ready. 
I've destroyed one machine (had to reinstall) and lost one morning in another because of it.
If it doesn't work keep it off. Please.

---

### Post by rg4w on 2012-02-06
> **cuby said:**
> I've destroyed one machine (had to reinstall) and lost one morning in another because of it.
What changes were being made with it which resulted in the bad systems?

---

### Post by ventrical on 2012-02-08
> **rg4w said:**
> What changes were being made with it which resulted in the bad systems?


  I just thought that this was interesting:

---

### Post by prusswan on 2012-02-08
So far from what I can see, the only thing CCSM 'kills' is Unity, that might not be so undesirable ;)

I do not believe a fancy looking gui will play a huge part in attracting and keeping users until the thing is already working right out of the box, it is probably more prudent to work on network related issues (there are quite a few that have not been satisfactorily addressed across several versions) since they are often a point of frustration even for experienced users when they are denied the internet while troubleshooting yet another issue.

---

### Post by ventrical on 2012-02-08
And yet  another stat for the bean counters ..

---

### Post by ventrical on 2012-02-08
> **prusswan said:**
> So far from what I can see, the only thing CCSM 'kills' is Unity, that might not be so undesirable ;)

  Well.. I like Unity a lot .. really ..   but I don't think that CCSM  is backward compatible in that sense.

  :)

---

### Post by prusswan on 2012-02-08
> **ventrical said:**
> I just thought that this was interesting:

That is something I never quite understand. I feel that CCSM is made a scapegoat for Unity's inability to protect itself after being shoved in as the one and only interface. Even without CCSM, Unity has problems even with Compiz (since it is a dependency)

---

### Post by ventrical on 2012-02-08
> **prusswan said:**
> That is something I never quite understand. I feel that CCSM is made a scapegoat for Unity's inability to protect itself after being shoved in as the one and only interface. Even without CCSM, Unity has problems even with Compiz (since it is a dependency)

  I'm with you 100% on that.   The nouveaus  just have this thing about trying to cram wayland into the bandwidth. CCSM is  proven (as is COMPIZ). I had assumed that 12.04 alpha/beta testing was to be a testing ground  to perfect Unity, not a slamfest on CCSM.

 As Wayland tries to seep in with more razzle and dazzle, real Unity bugs will get shelved once again, so , then , if CCSM is dissed , what will the devs have to blame then?

---

### Post by threuss on 2012-02-08
> **cuby said:**
> CCSM is not production ready. 
I've destroyed one machine (had to reinstall) and lost one morning in another because of it.
If it doesn't work keep it off. Please.

I second that!

---

### Post by ranch hand on 2012-02-08
I may be one of those that not only does not like compiz, but does not like Unity.

All that said, I have used both.

How anyone runs compiz without ccsm, the go to config tool, is beyond me.  Removing it will simply cripple compiz as a whole.

If Unity, a compiz plug in, is not compatible with ccsm then Unity needs fixing, not ccsm.  Let us get these things straight in our heads.

Compiz is a WM, ccsm configures the WM, Unity is a plugin for the WM.  Now. look at that list.

Removing the middle one is similar to someone with a new building saying that their roof doesn't work right so the wall studs should be removed to make the roof closer to the foundation.  Now it is true that this will accomplish this.  It is not true that it is a good idea.

---

### Post by cariboo on 2012-02-08
Ccsm does work, and doesn't need fixing, I use it to customize some unity settings, the problem is, it is to complicated for Ubuntu's target user, there have been many users, even in the development forums that have hosed their install, by indiscriminately trying the various settings that are available. As far as I can see the idea is to replace ccsm with a simpler tool, although exactly what that tool will allow the user to do isn't exactly clear yet.

The other problem is that the only developer is employed by Canonical, if someone else were to step up and take over maintaining and developing compizconfig-settings manager. I think everyone would be happy.

---

### Post by ventrical on 2012-02-08
> **ranch hand said:**
> I may be one of those that not only does not like compiz, but does not like Unity.

All that said, I have used both.

How anyone runs compiz without ccsm, the go to config tool, is beyond me.  Removing it will simply cripple compiz as a whole.

If Unity, a compiz plug in, is not compatible with ccsm then Unity needs fixing, not ccsm.  Let us get these things straight in our heads.

Compiz is a WM, ccsm configures the WM, Unity is a plugin for the WM.  Now. look at that list.

Removing the middle one is similar to someone with a new building saying that their roof doesn't work right so the wall studs should be removed to make the roof closer to the foundation.  Now it is true that this will accomplish this.  It is not true that it is a good idea.

  Nice write Ranch hand.    It makes me wonder just how unifying Unity is. I mean .. it is more or less CCSM that unifies the control between the compiz-core and unity-desktop.. so I don't get the detractor logic of some.

   Last I had looked the principle developer is hard at work on several compiz/ccsm/unity bugs ... so perhaps  patience may be a virtue here :)

---

### Post by ranch hand on 2012-02-08
> **ventrical said:**
> Nice write Ranch hand.    It makes me wonder just how unifying Unity is. I mean .. it is more or less CCSM that unifies the control between the compiz-core and unity-desktop.. so I don't get the detractor logic of some.

   Last I had looked the principle developer is hard at work on several compiz/ccsm/unity bugs ... so perhaps  patience may be a virtue here :)
As always in testing.

Beats throwing out the baby with the bath water.

---

### Post by VinDSL on 2012-02-09
> **ranch hand said:**
> Beats throwing out the baby with the bath water.
Heh!  Or... throwing the baby out, and keeping the bath water.  

LoL!  :D

---

### Post by prusswan on 2012-02-15
a little love for ccsm today:

```

Changes for the versions:
Installed version: 0.9.5.92-0ubuntu2
Available version: 0.9.5.92-0ubuntu3

Version 0.9.5.92-0ubuntu3: 

  [ Andrew Starr-Bochicchio ]
  * debian/patches/02_add_first_run_warning.patch:
   - Add a first run dialog providing a user warning.
  * debian/patches/03_disable_unity_checkbox.patch:
   - If in a Unity session, don't allow the user to disable
     Unity from main view.

```

---

### Post by PaulW2U on 2012-02-15
> **prusswan said:**
> a little love for ccsm today:
```

   - If in a Unity session, don't allow the user to disable
     Unity from main view.
```
Yes, I noticed that change earlier.

The check-box next to the Unity plug-in is unchecked when running Gnome Shell but is not even visible when running Unity.

---

### Post by mc4man on 2012-02-15
> **PaulW2U said:**
> Yes, I noticed that change earlier.

The check-box next to the Unity plug-in is unchecked when running Gnome Shell but is not even visible when running Unity.

It's still possible to disable inside the plugin window which isn't a bad thing, many 'issues' when enabling/disabling other plugins are caused by the unity plugin being enabled.
(so in some cases - disable unity, do whatever, re-enable unity & wait out the inevitable reset..

---

### Post by EgoGratis on 2012-02-15
I think you did the right thing!

-Unity settings landed in System Settings. This automatically drops CCSM usage quite substantialy.
-Ubuntu Tweak and MyUnity will probably be recommended as better options. This will help in two ways. A lot of feedback why somebody would rather use CCSM will be created and in the end i do believe this will come down to so little settings that they would easily be integrated in System Settings and/or UT & MU.
-It will turn out in my opinion that in some rare situations CCSM will still be needed and it would be a shame not to have it to change that settings and there are users that still heavily depend on CCSM and are skilled enough to use it.

Removed checkbox for Unity Plugin and note that trying "the impossible" could brake the display is fine too.

Great job!

---

### Post by ventrical on 2012-02-15
Great work!!

 A noob_ultimate tool!!  Now just work on the delivery and language. No more excuses.

---

### Post by philinux on 2012-02-16
[http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/](http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/)

Jorge's update.

---

### Post by mc4man on 2012-02-16
> **philinux said:**
> [http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/](http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/)

Jorge's update.

Hope he does complain about about g-s-d, & maybe sometime look up [what irrevocably means]("http://dictionary.reference.com/browse/irrevocable")

---

### Post by rg4w on 2012-02-16
> **philinux said:**
> [http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/](http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/)

Jorge's update.
Thanks for the link.  While it's unfortunate that some were rude with him over this, the final outcome seems quite optimal for everyone.  I appreciate that Jorge raised the issue.  I wish all controversies could have such productive results.

---

### Post by BeRoot ReBoot on 2012-02-16
Yep, I'm OK with the way this was handled. I wish the other dilemmas were solved this way instead of ripping out features and removing choice.

---

### Post by EgoGratis on 2012-03-13
> Better than removing CCSM from the users to use would be to fix Compiz Cube for example!

And indeed somebody did? I tried Unity 5.6 and tried if Compiz Cube would work and it did! 

Impressed!

---

### Post by rg4w on 2012-03-13
> **EgoGratis said:**
> And indeed somebody did? I tried Unity 5.6 and tried if Compiz Cube would work and it did! 

Impressed!
Very encouraging.  Jorge once mentioned to me that he'd like to see the Cube supported going forward since a lot of folks enjoy it, and perhaps it's now getting the love it deserves.

---

### Post by mc4man on 2012-03-13
> **EgoGratis said:**
> And indeed somebody did? I tried Unity 5.6 and tried if Compiz Cube would work and it did! 

Impressed!

There has been nothing released to fix the issues with cube/rotate since it broke with flashing during OO dev (compiz 0.9.4
Some hardware is unaffected, the majority are

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

The lead dev mentioned 4 months ago he had a fix but nothing has appeared yet

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862/comments/14)

So I'd term the response to this problem totally unimpressive

---

### Post by EgoGratis on 2012-03-13
If i remember correctly i had to copy/paste long command from Ask Ubuntu to enable Cube in previous (Unity) releases.

Something i guess did change because now i just press the button to enable Rotate Cube and it disables Desktop Wall too. Then i setup a grid of 4x1 instead of 2x2 workplaces and it worked.

There was some flashing and re-enabling Desktop Wall did require Log out/Log in but still something has changed because there was no (easy) way i could enable Rotate Cube without messing with the terminal in the past!

---

### Post by mc4man on 2012-03-13
> **EgoGratis said:**
> If i remember correctly i had to copy/paste long command from Ask Ubuntu to enable Cube in previous (Unity) releases.

Something i guess did change because now i just press the button to enable Rotate Cube and it disables Desktop Wall too. Then i setup a grid of 4x1 instead of 2x2 workplaces and it worked.

There was some flashing and re-enabling Desktop Wall did require Log out/Log in but still something has changed because there was no (easy) way i could enable Rotate Cube without messing with the terminal in the past!

Possibly there have been some improvement when enabling/disabling some plugins, if so minor & not confined to the wall cube/rotate deal

It has to do with plugin loading while the unity plugin is enabled, other plugins that _can_ cause compiz to reset or even hang include disabling grid, unityMT grab handles, png, possibly others. 

Myself always just first disable the unity plugin, then go about business & when done re-enable the unity plugin

---

### Post by snkiz on 2012-03-13
> **philinux said:**
> [http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/](http://www.jorgecastro.org/blog/2012/02/16/putting-their-own-money-where-your-mouth-is/)

Jorge's update.

Well if that isn't the biggest load of horse pucks I've ever seen, I don't know what is. Way to go Jorge, take credit for pissing off everyone in the name of getting a useless warning, (and an even more useless disabling on a checkbox.) Has anyone noticed that once you enter the unity plugin there is a big frackin button on the left to disable it? And a warning box? First off we know people generally don't read those, second that stupid box makes no mention that the only real risk is buggering unity. That's easy enough to fix, use gnome, or unity 2d. Undo what ever it is you did, and you back in business. Jorge didn't do anything useful except stir the hornets nest and create more bad blood. Compiz doesn't run any better, there are still stupid plugins in the core that shouldn't be there, the rest are still grouped in a few all or nothing packages. Useless eyecandy mixed with core functions. 
I'd let it go, with the thought at least someone is trying to improve things. But this is a bandaid on a gaping wound, and he has the nerve to sit on his high horse, "i had to do it, it was the only way to get action" Bull! like the rest, you just manipulated the community into fixing what wasn't broken, so we'd all look away while the real problems go unchanged. do what you like Jorge, but call a spade a spade.

---

### Post by ventrical on 2012-03-14
> **snkiz said:**
> Well if that isn't the biggest load of horse pucks I've ever seen, I don't know what is. Way to go Jorge, take credit for pissing off everyone in the name of getting a useless warning, (and an even more useless disabling on a checkbox.) Has anyone noticed that once you enter the unity plugin there is a big frackin button on the left to disable it? .

Yeah .. sort of defeats the whole purpose, whatever that purpose was. For the sake of Unity among the brothers and sisters, I am not going to rip into Jorge but I will say to those who have Ubuntu in  their blood to flatten and batten their previous versions because change is coming. I have been doing some experiments with some older hardware (SOYO mobo, 600MHz Celeron, 512MBsdram, ATI Rage Pro 128 (64mb)and 7200rpm baracuda and running Precise from alpha 2 I was able to get all those 3D games line Neverball, Neverputt, Brutal Chess .. etc.. working with the 3.2.0-12 kernel that comes with that alpha, but , as soon as you upgrade to current 3.2.0-18 then the whole graphical works are foo-barred. Those 3D games will not work (although Unity 2D works just fine). There has been a major regression to the Precise upgrade and anybody in a third-world country hoping to run the latest Ubuntu off of older, surplus hardware  can pretty well count their hardware as being obsolete , especially in the  kids games areas - and that goes for Edubuntu also!

---

### Post by cariboo on 2012-03-14
@ventrical, your problems with games, have nothing to do with ccsm, it sounds more like a graphics driver problem.

---

### Post by snkiz on 2012-03-14
disappointing none the less. when I started with Ubuntu (6.06) right up til 10.04 I was using almost those exact specs. (with less ram) Still have that board somewhere.

---

### Post by ventrical on 2012-03-14
> **cariboo907 said:**
> @ventrical, your problems with games, have nothing to do with ccsm, it sounds more like a graphics driver problem.

Apologies,

Wrong thread..

---

### Post by castrojo on 2012-03-14
> **snkiz said:**
> Well if that isn't the biggest load of horse pucks I've ever seen, I don't know what is. Way to go Jorge, take credit for pissing off everyone in the name of getting a useless warning, (and an even more useless disabling on a checkbox.)

The tool got some fixes to make it not crash when scrolling and a warning to tell people that it could break your computer, since people keep recommending the tool without that warning it makes sense to put it there.

> Has anyone noticed that once you enter the unity plugin there is a big frackin button on the left to disable it?

Nope, there isn't. It got removed, because it broke things. 


> Jorge didn't do anything useful except stir the hornets nest and create more bad blood. Compiz doesn't run any better, there are still stupid plugins in the core that shouldn't be there, the rest are still grouped in a few all or nothing packages. Useless eyecandy mixed with core functions. 

Bad blood? What are you talking about? There was a broken tool, I pointed it out, and people fixed it. I still think it sucks, but it's better than what we had before. 


> I'd let it go, with the thought at least someone is trying to improve things. But this is a bandaid on a gaping wound, and he has the nerve to sit on his high horse, "i had to do it, it was the only way to get action" Bull! like the rest, you just manipulated the community into fixing what wasn't broken, so we'd all look away while the real problems go unchanged. do what you like Jorge, but call a spade a spade.

This is an improvement, we have a tool that now has less of a chance of breaking someone's desktop. I'm sorry you feel that improving Ubuntu is manipulation, you might have to get used to that.

---

### Post by ventrical on 2012-03-14
> **castrojo said:**
> The tool got some fixes to make it not crash when scrolling and a warning to tell people that it could break your computer, since people keep recommending the tool without that warning it makes sense to put it there.



Nope, there isn't. It got removed, because it broke things. 




Bad blood? What are you talking about? There was a broken tool, I pointed it out, and people fixed it. I still think it sucks, but it's better than what we had before. 




This is an improvement, we have a tool that now has less of a chance of breaking someone's desktop. I'm sorry you feel that improving Ubuntu is manipulation, you might have to get used to that.


Click on that Jorge.

---

### Post by castrojo on 2012-03-14
Oh I thought you meant the checkbox on the screen above that, where there used to be a checkbox, good catch, I'll report a bug!

---

### Post by mc4man on 2012-03-14
> **castrojo said:**
> Oh I thought you meant the checkbox on the screen above that, where there used to be a checkbox, good catch, I'll report a bug!

Why would you do that - there's no reason to remove all means to disable the unity plugin in ccsm, particularly one where there is virtually no possibility of inadvertently disabling the plugin.

The reasons for keeping that interior checkbox far outweigh any possible 'gain'

---

### Post by ventrical on 2012-03-14
> **mc4man said:**
> Why would you do that - there's no reason to remove all means to disable the unity plugin in ccsm, particularly one where there is virtually no possibility of inadvertently disabling the plugin.

The reasons for keeping that interior checkbox far outweigh any possible 'gain'

 Your right and I already experiemented with it, turned it off,  the unity laucher disappeared, ticked it back on and it instananeously reappeared so there is no bug there.

---

### Post by ventrical on 2012-03-14
> **castrojo said:**
> Oh I thought you meant the checkbox on the screen above that, where there used to be a checkbox, good catch, I'll report a bug!

It's not a bug Jorge. Tic it off and then tic it back on again.

---

### Post by mc4man on 2012-03-14
> **mc4man said:**
> 
The reasons for keeping that interior checkbox far outweigh any possible 'gain'

I'm going to give one simple example, using the 'infamous'  wall to cube switch

Open ccsm
Disable unity plugin
Disable wall
Enable cube & rotate
Re-Enable unity

There will be a slight period while the plugins are sorted, then possibly a screen flash & that's it, done, nothing broken, ect.

---

### Post by rg4w on 2012-03-14
> **mc4man said:**
> I'm going to give one simple example, using the 'infamous'  wall to cube switch

Open ccsm
Disable unity plugin
Disable wall
Enable cube & rotate
Re-Enable unity

There will be a slight period while the plugins are sorted, then possibly a screen flash & that's it, done, nothing broken, ect.
Recipe reproduced on most machines here.

Until Unity's error-checking is brought up to the level needed to support the Compiz it relies on, it may be better to leave that last checkbox in place for now.

---

