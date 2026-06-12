---
title: "Display Microsoft fonts like on Windows"
date: 2006-07-03
forum: Tutorials
---

### Post by calande on 2006-07-03
**[COLOR="DarkRed"]This tutorial now has a web site: [http://www.sharpfonts.com/](http://www.sharpfonts.com/)[/COLOR]** :)

I tweaked the fontconfig XML files so that fonts look like on Windows. This code is borrowed from [PC-BSD](http://www.pcbsd.org). First, let's install the Microsoft fonts. You have 2 ways of doing so:

Either download the [fonts](http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz) into your home directory and install them on your system:

```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```

Or, enable non-free, universe and multiverse repositories and install the Microsoft fonts:

```
sudo apt-get install msttcorefonts
```

You now have the Microsoft fonts installed. Let's configure your system now.

Download the [xml files]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz") and extract the file into /etc/fonts/ as root:

```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

Log out from Ubuntu and relog in. Here's how your desktop will look like:

[[IMG]http://img412.imageshack.us/img412/6972/ubuntu5ui.th.png[/IMG]](http://img412.imageshack.us/img412/6972/ubuntu5ui.png)

It's a lot more complex than disabling antialiasing at small font sizes :)

[SIZE="4"][DIGG IT!]("http://digg.com/linux_unix/Display_Microsoft_fonts_in_Unix_like_on_Windows")[/SIZE]

---

### Post by tep200377 on 2006-07-04
APt get didnt find the package ?! [-(

---

### Post by DC@DR on 2006-07-04
That works perfectly nice, dude, thanks a lot :)

---

### Post by tep200377 on 2006-07-04
brp@brp-laptop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate


:p

---

### Post by newbie2 on 2006-07-04
[QUOTE=tep200377]brp@brp-laptop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate


:p[/QUOTE]

yep...that's also what i get :-?

---

### Post by digby on 2006-07-04
[quote=tep200377]APt get didnt find the package ?![/quote] 
You have to enable the extra apt repositories first.  From the OP:> Enable non-free, universe and multiverse repositories.Make sure your /etc/apt/sources.list has these lines.

deb [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security universe multiverse

If you find them and they have a '#' in front, you have to remove that.  Then run ```
sudo apt-get update
```Then you should be able to install the font package.

Edit:  If you don't know how to edit your sources.list file, see [here.]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

---

### Post by petervk on 2006-07-04
Do you have the universe and multiverse repo's enabled? Because that would give you a similar error. Try to enable the universe and multiverse and try that command again.

---

### Post by tep200377 on 2006-07-04
I gotta say, I really love it when people help me out ;) 

Im a newbie on ubuntu. I've tried slackware and other distroes before, but ubuntu really made me make the switch .. 

\\:D/

---

### Post by newbie2 on 2006-07-04
[QUOTE=digby]You have to enable the extra apt repositories first.  From the OP:Make sure your /etc/apt/sources.list has these lines.

deb [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security universe multiverse

If you find them and they have a '#' in front, you have to remove that.  Then run ```
sudo apt-get update
```Then you should be able to install the font package.

Edit:  If you don't know how to edit your sources.list file, see [here.]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")[/QUOTE]

i use dapper kubuntu and it works now ...thanx very much....

---

### Post by lepre on 2006-07-04
half-working for me, maybe it's because i did an other fix and them don't fit togheter?

---

### Post by Hairy_Palms on 2006-07-04
nice howto, definately changes the font, im just confused though lol i genuinely cant decide if i like it better before or after :D

---

### Post by madscience on 2006-07-04
I think I liked it better before, on my laptop's LCD... could someone give me a hand to revert to the original config files... (ie post their's)?

Thanks.

---

### Post by barbarian on 2006-07-05
Thanx for configs. Tried with Kubuntu 6.06 Desktop(Live) CD on laptop - worked perfectly.

---

### Post by calande on 2006-07-05
To revert, erase the file local.conf

---

### Post by calande on 2006-07-05
Firefox is the only application that doesn't take this configuration into account, and uses antialiasing for all fonts at any size. Does some one know how to solve this problem? I tried this setting in the about:config options:

```
font.antialias.min = 20
```

Which had no effect... Any idea?
Thanks,

---

### Post by eradicator_006 on 2006-07-09
> **calande said:**
> Firefox is the only application that doesn't take this configuration into account, and uses antialiasing for all fonts at any size. Does some one know how to solve this problem? I tried this setting in the about:config options:

```
font.antialias.min = 20
```

Which had no effect... Any idea?
Thanks,
yeah same problem here. openoffice.org is also ignoring these customizations.  i dont use OO much so I can live with that.  i do use firefox regularly and would really like to fix the fonts there.

---

### Post by Psquared on 2006-07-09
Hmmm.... in Dapper I don't have a /etc/fonts folder. Should I create one?

---

### Post by crazygamer on 2006-07-10
> **eradicator_006 said:**
> yeah same problem here. openoffice.org is also ignoring these customizations.  i dont use OO much so I can live with that.  i do use firefox regularly and would really like to fix the fonts there.

Yeah, any help on "fixing" Firefox would be great! I also noticed that Yelp (if you go to System -> About Ubuntu) also anti-aliases that help despite AA being off in my Fonts prefs.

---

### Post by eradicator_006 on 2006-07-10
> **crazygamer said:**
> Yeah, any help on "fixing" Firefox would be great! I also noticed that Yelp (if you go to System -> About Ubuntu) also anti-aliases that help despite AA being off in my Fonts prefs.
I have the same thing in yelp.  There is one difference between what's happening in yelp and what's happening in firefox....the menu (ie file, edit,etc) is anti-aliased and the menu in yelp is not anti-aliased.  I use thunderbird for email and newsgroups and everything looks great with that program.

---

### Post by calande on 2006-07-10
Is there a bug tracker or wishlist at Ubuntu?

---

### Post by desperado666 on 2006-07-10
Now i need a Howto render fonts like a MAC

---

### Post by calande on 2006-07-11
Ok, I *finally* found a solution. I updated my XML files, please go ahead and follow the [original tutorial](http://ubuntuforums.org/showthread.php?t=208396) again. Now fonts in Firefox are going to look good, just like in Windows :)

Original thread:
[http://forums.pcbsd.org/viewtopic.php?p=25646](http://forums.pcbsd.org/viewtopic.php?p=25646)

---

### Post by barbarian on 2006-07-11
cool, thanks, it worked:)

---

### Post by memos on 2006-07-11
Hi guys i take this error> Extraction not performed

You don't have the right permissions to extract archives in the folder "/etc/fonts".Why?I do not have other user.

---

### Post by calande on 2006-07-11
Nope, you need root privilege. Here's how you would do:
```
sudo tar -xvjpf nicefonts.tbz /etc/fonts/
```
And type your root password when requested ;)

---

### Post by memos on 2006-07-11
Now i take this > tar: nicefonts.tbz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /etc/fonts: Not found in archive
tar: Error exit delayed from previous errors


---

### Post by calande on 2006-07-11
Ok, where did you put your "nicefonts.tbz" file? I'll assume you stored in your Desktop. If so, here's what you're gonna do instead:

```
cd ~/Desktop
sudo tar -xvjpf nicefonts.tbz /etc/fonts/
```

---

### Post by memos on 2006-07-11
In my desktop yes but error again > tar: /etc/fonts: Not found in archive
tar: Error exit delayed from previous errors

---

### Post by eradicator_006 on 2006-07-11
Works perfect now!  How did you fix it?  I spent several hours trying to make firefox look "good" and got nowhere.

---

### Post by crazygamer on 2006-07-11
I also fixed mine. Before I had my font config files in /etc/fonts which worked for the rest of the system but not firefox or yelp. I copied them to ~/.fonts and that fixed those 2 programs as well.

---

### Post by calande on 2006-07-11
> **memos said:**
> In my desktop yes but error again
Well, you'll have to find a way to extract this file into your /etc/fonts/ directory as root...

I don't know how to help at this point :(

---

### Post by calande on 2006-07-11
Oops! The code is actually:```
sudo tar -xvjpf nicefonts.tbz -C /etc/fonts/
```

Sorry!

---

### Post by Mr_HeNtAi on 2006-07-11
Great information! Thanks for the post.

---

### Post by memos on 2006-07-12
Done.I fix with
```
cd ~/Desktop
```
and then
```
sudo tar -xvjpf nicefonts.tbz -C /etc/fonts/
```
Thaks man =D> =D> =D>

---

### Post by PingunZ on 2006-07-12
Great guide easy to follow, clearly and a lil bit of explanation ;)

TY :KS 

edit :: how can I undo this ??? I really don't like these fonts :p



Grtz PingunZ

---

### Post by Urmas on 2006-07-12
Great! Thanks!

\\:D/ \\:D/ \\:D/

---

### Post by PingunZ on 2006-07-12
Is it normal that some apps like gedit etc dont work anymore and that the update manager really looks ugly ?

Plz tell me how to undo this ... :p

Grtz PingunZ

---

### Post by calande on 2006-07-12
Sure, if you run into problems or if it doesn't look like the screenshots, just remove /etc/fonts/local.conf and uninstall the Microsoft Fonts ;)

---

### Post by MellonCollie on 2006-07-12
Nice, thanks!

---

### Post by afterxleep on 2006-07-12
To solve the issue in OpenOffice, just go to Tools > Options and untick the Antialias check box.   Or even better, set it to antialias small fonts, like 12px or less.

---

### Post by BIGtrouble77 on 2006-07-12
This font config is most excellent.  Thanks calande, you did a phenominal job.

---

### Post by harissza on 2006-07-13
Hi All,

I applied these new updates now:

[UPGRADE] gimp 2.2.11-1ubuntu3 -> 2.2.11-1ubuntu3.1
[UPGRADE] gimp-data 2.2.11-1ubuntu3 -> 2.2.11-1ubuntu3.1
[UPGRADE] gimp-python 2.2.11-1ubuntu3 -> 2.2.11-1ubuntu3.1
[UPGRADE] libgimp2.0 2.2.11-1ubuntu3 -> 2.2.11-1ubuntu3.1
[UPGRADE] libsmbclient 3.0.22-1ubuntu3 -> 3.0.22-1ubuntu3.1
[UPGRADE] libxine-main1 1.1.1+ubuntu2-7.1 -> 1.1.1+ubuntu2-7.2
[UPGRADE] linux-kernel-devel 2.6.15-25.43 -> 2.6.15-26.44
[UPGRADE] linux-restricted-modules-common 2.6.15.11-2 -> 2.6.15.11-3
[UPGRADE] login 1:4.0.13-7ubuntu3.1 -> 1:4.0.13-7ubuntu3.2
[UPGRADE] openoffice.org 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-base 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-calc 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-common 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-core 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-draw 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-evolution 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-gnome 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-gtk 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-impress 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-java-common 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-l10n-en-us 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-math 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] openoffice.org-writer 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] passwd 1:4.0.13-7ubuntu3.1 -> 1:4.0.13-7ubuntu3.2
[UPGRADE] python-uno 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1
[UPGRADE] samba-common 3.0.22-1ubuntu3 -> 3.0.22-1ubuntu3.1
[UPGRADE] smbclient 3.0.22-1ubuntu3 -> 3.0.22-1ubuntu3.1
[UPGRADE] ttf-opensymbol 2.0.2-2ubuntu12 -> 2.0.2-2ubuntu12.1

Nothing I can see relating to fonts BUT everything has gone worse. I can copy the original fonts folder back but I get only the ugly default fonts back. I want these nice ones back again! Any idea? It was fabulous for a week on my dapper...

Thanx

Adam

---

### Post by gabrieliscool on 2006-07-16
This Doesn't work with the Suse Linux Enterprise Desktop (SLED) Menu.
I Tried It And I Had Bad Font Problems.

BTW, If You Want To Install the SLED Menu, go to
[http://angelicpenguins.blogspot.com/2006/07/sled-menu-for-ubuntu-uslab-now-in-repo_14.html](http://angelicpenguins.blogspot.com/2006/07/sled-menu-for-ubuntu-uslab-now-in-repo_14.html)

---

### Post by calande on 2006-07-16
I just updated the files, now very tiny bold Arial and Verdana fonts are aliased for better readability :)

As far as SLED, I have no idea, if some one uses it and has a fix, you're mostly welcome ;)

---

### Post by TheMono on 2006-07-18
This seems to have caused quite an issue - it's hard to explain this, but now my computer is rendering only the left hand side of each line, until I select it, and upon selection, it fixes itself.

For example, if I bring up a menu, go to the "sound and video" section, I can see "GXine" in the menu. If I then run my mouse over that (ie, without clicking, just making the background go dark - what do you call doing that lol), it changes then to "GXine Movie Player" - ie, it renders the full string of text.

Ideas? I do much prefer the fonts like this and I'd like to keep it if I can get rid of this problem.

Oh, and also, it happens in almost everything - the GKSudo dialogbox, in Evolution, etc.

---

### Post by rniella on 2006-07-19
This is great !!!  I`ve been messing around with the fonts for a while now since I had the k, x issue and found a liiitle bit of improvement installing windows fonts and adjusting the anti-alias, but your  How-to was a great improvement for me, many thanks !!!

RN

---

### Post by calande on 2006-07-19
You welcome! I think it should be integrated into default installation :)

---

### Post by LamB on 2006-07-20
Thanks a lot!!! this REALLY improves font display...:D

---

### Post by BanskuZ on 2006-07-20
Nice HOWTO. But I have "little" problem with firefox:

[[IMG]http://img232.imageshack.us/img232/3152/fontsdl8.th.png[/IMG]](http://img232.imageshack.us/my.php?image=fontsdl8.png)

---

### Post by calande on 2006-07-20
Ok, I think I know what the problem is. Go to your Firefox font configuration and select generic family fonts, for monospace you will select "Monospace" instead of what there is currently.

---

### Post by BanskuZ on 2006-07-20
> **calande said:**
> Ok, I think I know what the problem is. Go to your Firefox font configuration and select generic family fonts, for monospace you will select "Monospace" instead of what there is currently.

Thanks. :)

---

### Post by Burgresso on 2006-07-20
Got halfway through, then I noticed the site holding the XML files is down...hope its ups soon, but here's a tentative thanks!

---

### Post by Spellweaver on 2006-07-21
Yes, the with the xml files is stil down. I'm glad I'm not the only one with this problem :rolleyes:

---

### Post by Burgresso on 2006-07-21
Cool! it's back as I post this. I'll have to try this later, but at least I was able to snag the XML file.

---

### Post by Burgresso on 2006-07-21
Awesome! Thank you very much - looks great and reduces eye strain!!!

Any advice on how to customize the output - for example, changing the size at which font is aliased?

---

### Post by fatsheep on 2006-07-21
I've installed the microsoft core fonts and they display just like they do in Windows already.  What do these XML files do?

---

### Post by Burgresso on 2006-07-21
They make it so that smaller fonts - around 16px or so or smaller - are *not* aliased, but bigger fonts are.

---

### Post by fatsheep on 2006-07-22
Wow you're right fonts look much nicer now.  :p  Very nice How To!

---

### Post by yopnono on 2006-07-22
Hi. Nice work. But.. I have notice that the ARIAL BOLD looks better if you change this from 11px to 14px. Since the BOLD looks blurry when they are less then 14px. Or it could be just me.
	```
<!-- Arial bold not italic less than 14px has antialias off -->

<match target="font" >
	<test name="family" >
		<string>Arial</string>
	</test>
	<test compare="more" name="weight" >
		<int>100</int>
	</test>
	<test compare="eq" target="pattern" name="slant" >
		<const>roman</const>
	</test>
	<test compare="less" name="size" qual="any" >
		<double>14</double>
	</test>
	<edit mode="assign" name="antialias" >
		<bool>false</bool>
	</edit>
</match>

<match target="font" >
	<test name="family" >
		<string>Arial</string>
	</test>
	<test compare="more" name="weight" >
		<int>100</int>
	</test>
	<test compare="eq" target="pattern" name="slant" >
		<const>roman</const>
	</test>
	<test compare="less" name="pixelsize" qual="any" >
		<double>14</double>
	</test>
	<edit mode="assign" name="antialias" >
		<bool>false</bool>
	</edit>
</match>
```

---

### Post by Burgresso on 2006-07-22
yopnono,

what file are you editing?

---

### Post by yopnono on 2006-07-22
/etc/fonts/msfonts-rules.conf

---

### Post by mario8723 on 2006-07-22
> **tep200377 said:**
> I gotta say, I really love it when people help me out ;) 

Im a newbie on ubuntu. I've tried slackware and other distroes before, but ubuntu really made me make the switch .. 

\\:D/
I couldn't agree with you more!

These fonts look AWESOME. Thanks so much for this tutorial. These forums and community are the biggest reasons I chose and stuck with Ubuntu for my distro!

---

### Post by calande on 2006-07-22
That's true. I won't bash any other Linux distro, most of them are elitist. Ubuntu is human and focused at helping other human beings, whoever they are.

---

### Post by SuperMike on 2006-07-22
Actually, not to be to contra here, but I find the Bitstream Vera fonts display so much smoother than the Microsoft fonts. The MS fonts don't look too much different than them -- the MS fonts look less anti-aliased.

I, at one time, thought this would be the way to go, but when I installed it, I wanted to go back to the way the system comes by default.

---

### Post by calande on 2006-07-22
I am also a CentOS user, and I can't stand the antialiased fonts that CentOS has, it's like default Ubuntu, it hurts my eyes, I can't concentrate on what I read. First think I do is change the fonts to have the MS fonts instead of whatever comes by default on Linux.

---

### Post by srunni on 2006-07-22
Wow.

_Very_ nice. That's all I have to say. As much as some might hate to admit it, M$ actually did a pretty good job with the fonts, and I've been missing them. They're a lot easier on the eyes than the Ubuntu default.

Thank you _very_ much.

---

### Post by Cruxic on 2006-07-24
Wow.  This is a lot nicer in my opinion.  Of course, I am just now switching from Windows.  Blurry and cookie crumb font rendering has been one of my frustrations with Linux in the past.  Can anybody recommend some free fonts that look good on the screen without anti-aliasing?  Somebody mentioned Bitstream Vera?

I tend to agree with Joel regarding anti-aliasing
[http://www.joelonsoftware.com/articles/fog0000000041.html](http://www.joelonsoftware.com/articles/fog0000000041.html)

---

### Post by calande on 2006-07-25
AFAICK, only the MS fonts look good when aliased. Bitstream  and DejaVu will look bad.

---

### Post by gmc on 2006-07-27
> **calande said:**
> You welcome! I think it should be integrated into default installation :)

This howto ROCKS Thanks calande :D ! ..and I whole heartedly agree.

G.

---

### Post by Burgresso on 2006-07-28
After setting this up, I've noticed that some fonts on the system - such as arial and (times/new) roman are aliased still - any advice on making it so these are aliased too?

regards and thanks

burgresso

---

### Post by calande on 2006-07-28
Yes, they are actually supposed to be aliased and hinted at small font sizes :)

---

### Post by Burgresso on 2006-07-28
calande,

thanks for your response - to clarify a bit what I meant - I wasnt to clear b4:

Arial always looks good, becuase the smaller sizes are not aliased. But courier and times don't always, so I was wondering if there is a portion of the XML file of somethinng I could edit to make it not alias at around 12px or something.

again,

thanks

---

### Post by calande on 2006-07-28
Hi, I see. Actually Courier and Times are always antialiased and autohinted because they don't have hints. The Microsoft fonts Courier New and Times New Roman have hints and therefore I can turn off antialising under 16px for both of them and turn on hinting, this is why they look just like on Windows.

It seems you are using Unix fonts (Courier and Times) thinking you're using the Microsoft fonts :)

---

### Post by shalinmangar on 2006-07-28
Can I know if there's something special needed to be done to un-install these fonts from my system?

---

### Post by Burgresso on 2006-07-29
> **calande said:**
> It seems you are using Unix fonts (Courier and Times) thinking you're using the Microsoft fonts :)

Ah ha! Thanks calande -

How do I make sure I'm using the MS Fonts? I set up the XML file as instructed.

---

### Post by IYY on 2006-08-01
Very nice... I'm not sure if I like it or not, but it sure did the trick.

---

### Post by ounas on 2006-08-02
Thanks Calande

:D :)

---

### Post by calande on 2006-08-02
> **Burgresso said:**
> Ah ha! Thanks calande -

How do I make sure I'm using the MS Fonts? I set up the XML file as instructed.

You just have to use default font configuration in Gnome and Firefox: select generic font families (sans serif; serif; monospace...)

---

### Post by Rackerz on 2006-08-04
Wow I can read again! Lol. Thanks a lot for this, always been trying to find a way to display fonts as they are in Windows. 

Thanks!

EDIT: What are the default, 'Application Font' and 'Document Font' in Windows? Bitstream Vera Sans Roman isn't looking to sharp at the minute.

---

### Post by mkljun on 2006-08-06
> **desperado666 said:**
> Now i need a Howto render fonts like a MAC

[http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/](http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/)

---

### Post by puelly on 2006-08-11
i forgot to make a backup of my original /etc/fonts folder.  Can someone please email it to me or tell me how it can be restored with apt. thanks.

grenadian1 at gmail dot com

---

### Post by dbmet on 2006-08-12
Wow...I can read again..thanks ..

---

### Post by denday on 2006-08-17
thanks, i love it. :D

---

### Post by Irony on 2006-08-17
This works great - everything is clear after some fiddling with font preferences.

The trouble with some of the default Ubuntu fonts is that the anti-aliasing fools the eye into thinking it is not focussed, so the eye keeps trying to focus which is fatiguing.

---

### Post by eradicator_006 on 2006-08-17
Fonts don't look so good since installing today's updates.  I've tried reinstalling the xml files and rebooting....that did not help.

---

### Post by BFGod on 2006-08-18
Yes, same happened here after todays update. It's because libfreetype6, so I just downgoraded it and all is well again. So you just downgrade it to the version you had before, and the problem will be solved, atleast until original poster writes a fix for this (at least I hope he will).

BTW, my first post :) Hello to everyone in Ubuntu community.

---

### Post by calande on 2006-08-18
Hey, please give me the detailed instructions, what to type, where to download, etc... And I'll update my original post for you guys :)

---

### Post by glennric on 2006-08-18
If you delete the files:
```

alias.conf
freefonts-rules.conf
local.conf
misc.conf
msfonts-rules.conf

```
from /etc/fonts/
(i.e. the files that this howto tells you to put in)
then your fonts will look better.  That is since the latest upgrade to libfreetype from the xgl and compiz repositories.

These files will most likely need to be modified to work now.  It is really to bad.  They made the fonts look great, right up until these updates.

---

### Post by marin.r on 2006-08-19
Hi guys, I'm totally updated & followed the howto and it worked.
However, I reverted to original, as this made everything look so MS-ish I couldn't stand it.
My question is to Irony, who said that 
> 
The trouble with some of the default Ubuntu fonts is that the anti-aliasing fools the eye into thinking it is not focussed, so the eye keeps trying to focus which is fatiguing.
Are you certain that's the case ? I mean if the default is bad for the eyes in such way I really will put the windows look back, but its hard for me to believe it?

---

### Post by glennric on 2006-08-19
> **marin.r said:**
> Hi guys, I'm totally updated & followed the howto and it worked.
However, I reverted to original, as this made everything look so MS-ish I couldn't stand it.
My question is to Irony, who said that 

Are you certain that's the case ? I mean if the default is bad for the eyes in such way I really will put the windows look back, but its hard for me to believe it?

If you are completely updated and using this update with actual microsoft fonts this wouldn't work for you.  You would see the worst font display you have ever seen.  They would not even look close to MS-ish.  This howto still seems to work well with non MS fonts.

Edit:  After some more testing I see that all fonts suck with this howto after all updates are applied.

---

### Post by TOPPEL on 2006-08-21
i would like to restore the font rendering to ubuntu.  its not looking so good for me over here.  

thank you

---

### Post by marin.r on 2006-08-30
> **glennric said:**
> If you are completely updated and using this update with actual microsoft fonts this wouldn't work for you.  You would see the worst font display you have ever seen.  They would not even look close to MS-ish.  This howto still seems to work well with non MS fonts.

Edit:  After some more testing I see that all fonts suck with this howto after all updates are applied.

I was totally updated, and maybe not using compiz etc is what's different between our setups. The fonts got 100% like in windows.

---

### Post by snowmann on 2006-09-13
Hi

It looks realy great!
Only OpenOffice looks bad :( Why?

SnowMann

---

### Post by calande on 2006-09-13
This tutorial is for PC-BSD, but you'll find some useful information: [http://faqs.pcbsd.org/2_288_en.html](http://faqs.pcbsd.org/2_288_en.html)

---

### Post by snowmann on 2006-09-14
@calande
thank you for the link.
It's really crazy. I have deactivate "Use system fonts for user interface" and now it looks perfect :)

PS: Sorry for my english

---

### Post by calande on 2006-09-14
Yes, OpenOffice.org uses its own fonts rendering engine. That's sad.

---

### Post by Burgresso on 2006-09-15
Would this work on other linux distros too?

---

### Post by alex1973 on 2006-09-16
Looks great, except for Firefox tab fonts (unread tabs) - very blury.
I've also noticed that Google's Picasa font got blury.

---

### Post by calande on 2006-09-16
Could you show us a screenshot?

---

### Post by lammer on 2006-09-17
Same problem: Some fonts get blurred, and not only on firefox:

Maybe it's because I've allready changed my font config with the ubuntu font manager?

[[IMG]http://img434.imageshack.us/img434/8153/screenshotzj8.th.png[/IMG]](http://img434.imageshack.us/my.php?image=screenshotzj8.png)

---

### Post by calande on 2006-09-17
Do you have a screenshot at the 1:1 scale (not resized) please?
You need to use generic font families (sans-serif, monospace, serif, cursive, etc...) and not regular font names such as Tahoma, although Microsoft fonts should look good anyway :)

---

### Post by lammer on 2006-09-18
Yep! My fault, imageshack do some kind of resize, or at least I don't know how to put the original one on it. This is the screenshot again:

[[IMG]http://images6.theimagehosting.com/screenshot.1d8.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=screenshot.1d8.png)

Anyway I've followed this tutorial instead and now my fonts look pretty cool on my 19"LCD monitor:

[http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/](http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/)

This is how it looks right now. But with "the other patch":

[[IMG]http://images6.theimagehosting.com/screenshot2.617.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=screenshot2.617.png)

I think I've allready done, but in case I can help you fixin this extrange issue with some blured fonts, I'll be over here :-)

---

### Post by yopnono on 2006-09-19
> **lammer said:**
> Yep! My fault, imageshack do some kind of resize, or at least I don't know how to put the original one on it. This is the screenshot again:

[[IMG]http://images6.theimagehosting.com/screenshot.1d8.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=screenshot.1d8.png)

Anyway I've followed this tutorial instead and now my fonts look pretty cool on my 19"LCD monitor:

[http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/](http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/)

This is how it looks right now. But with "the other patch":

[[IMG]http://images6.theimagehosting.com/screenshot2.617.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=screenshot2.617.png)

I think I've allready done, but in case I can help you fixin this extrange issue with some blured fonts, I'll be over here :-)

Try to use SANS instead of tahoma and the font fix in this thread.

---

### Post by lammer on 2006-09-20
> **yopnono said:**
> Try to use SANS instead of tahoma and the font fix in this thread.
So you think it's better this fix than the other one. I will give a try in this case. You said Sans instead of tahoma... I wonder why, but I'll try with sans anyway.

I'll check in the next days the two "fixes", and try to post a screenshot of each one. Cheers!!

---

### Post by yopnono on 2006-09-20
> **lammer said:**
> So you think it's better this fix than the other one. I will give a try in this case. You said Sans instead of tahoma... I wonder why, but I'll try with sans anyway.

I'll check in the next days the two "fixes", and try to post a screenshot of each one. Cheers!!

Well I prefer this fix and Sans = Clear sharp fonts.

But it could have something to do with your theme for firefox.

see my img, it's sans and this fix, and some small modifications.

---

### Post by alex1973 on 2006-09-21
Sorry for delay.

Here's the snapshot: [[IMG]http://images6.theimagehosting.com/blury-italic.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=blury-italic.png)

But, I have realized that this is happening when Firefox is set to use italic for unread tab (TabMix Plus -> Display -> Tab -> Customize Style -> Unread tabs -> Italic).

I've also noticed the blurry text on Picasa running on Windows also.

---

### Post by TigPT on 2006-10-17
sory for open your post again, but i made your tuturial, and i have to say tha is very cool, and not only easy and fast to do, it works fine and gives beter X11 aspect.

But, i got some trobles in gDesklets leters after aply it, and maybe you can help me fix it..

thks for all,
TigPT

---

### Post by Newur on 2006-10-28
Hi,

I installed your files and it almost worked very great. But last time I recognized some website fonts looking very terribly. After some testings i found out, that the bugs disappear, when I remove your files.

For example check out this page:

[http://animeboard.at/index.php]("http://animeboard.at/index.php")

Bug is tested on 2 PCs, using Dapper Drake and Edgy, with Firefox 1.5 and Firefox 2.0


Greetings
Newur

---

### Post by calande on 2006-10-28
If you use Firefox, you need to define a minimum font size (ie: 10px). Works great in Opera.

---

### Post by Newur on 2006-10-28
Ya, in Opera it looks great, that's right.

But changing/defining a minimum font size in Firefox didn't fix the problem. :(

---

### Post by turbojugend_gr on 2006-11-20
I also prefer mac fonts, and some Linux fonts, definately not MS ones, they are so ugly, well rendered but still so far from spontaneous... 

FreeSerif is the Best font ever, no wonder all movie subtitles use it.

---

### Post by calande on 2006-11-20
They look good, but not as good as the MS fonts at small sizes.

---

### Post by giruzz on 2006-11-21
Done but got this error at the end...

comic32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

---

### Post by [MArCoZ] on 2006-11-21
Hi all, Im new on this forum!

Calande, I've followed your guide on my edgy, but after login/logout nothing changes.
Is there something else to do, to get my fonts as in your image?

Thanks and best regards to all members!

---

### Post by yopnono on 2006-11-30
> **Newur said:**
> Hi,

I installed your files and it almost worked very great. But last time I recognized some website fonts looking very terribly. After some testings i found out, that the bugs disappear, when I remove your files.

For example check out this page:

[http://animeboard.at/index.php]("http://animeboard.at/index.php")

Bug is tested on 2 PCs, using Dapper Drake and Edgy, with Firefox 1.5 and Firefox 2.0


Greetings
Newur

It's something in the misc.conf in /etc/fonts/ Just rename it, and you will be fine. I will check why it's like that.

---

### Post by yopnono on 2006-11-30
Ok I did change the misc.conf and attached the file. 
Change:
```
<int>100</int>
``` 
to 
```
<int>10</int>
``` 


```
<!--  Fixed spacing for monospace -->

<match target="pattern" name="family" >
	<test name="family" qual="any" >
		<string>monospace</string>
	</test>
	<edit mode="assign" name="spacing" >
		<int>10</int>
	</edit>
</match>
```

Test against this page if you like. before and after 
[http://www.datanom.net/tptest-gui/about.html](http://www.datanom.net/tptest-gui/about.html)

---

### Post by calande on 2006-11-30
Nice! Thanks for this fix! I updated the downloadable files on my server, when people download these new files, the above page should look good now!

---

### Post by mthakur2006 on 2006-12-01
Thanks, dat was nice! :D

---

### Post by bodhi.zazen on 2006-12-02
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by yopnono on 2006-12-09
@calande
You say that the fonts should go in to
```
/usr/X11R6/lib/X11/fonts/TTF/
```
But the fonts are normally in 
```
/usr/share/fonts/truetype
```
But I guess it doesn't make any different s

---

### Post by emergence on 2006-12-11
After installing windows fonts and the scripts you provided, the fonts in Ubuntu are exactly like Windows fonts without cleartype(very crisp). Is there a font smoothing algorithm for Ubuntu (or Linux in general) that is similar to cleartype? The font smoothing and hinting options for Ubuntu for don't work all that well... they're not as crisp and smooth as Windows fonts with cleartype.

---

### Post by ajm2005 on 2006-12-12
:)

---

### Post by Falcorian on 2006-12-22
Guide worked perfectly for me! Thanks!

---

### Post by calande on 2006-12-22
> **ajm2005 said:**
> the trick is to get tahoma from a windows installation (it isn't included in the ms core fonts download package). Used with the method in this tip/ tutorial, things look just like a windows installation - i.e., crisp, non-blurred tahoma as the default system font.

Actually the original post offers two methods to install the fonts. If you download the [fonts pack]("http://www.auriance.com/docs/fonts/msfonts.tbz"), it does include Tahoma ;)

---

### Post by nmincone on 2006-12-22
I use either Automatix2 or EasyUbuntu to install not only the other font families mentioned here but all the media codecs and players and plug-ins as well. It makes working in Ubuntu much more like working in Windows altogether.

---

### Post by logos34 on 2006-12-22
Thanks Calande!

That simple fontconfig fix sharpened things up quite a bit!  Now tahoma renders crisply almost (but not exactly) as it does in windows.  Web page fonts (except bold urls) much improved.

---

### Post by graficus on 2006-12-25
now everything looks like its windows 2000. i was hoping for xp cleartype look.

---

### Post by frotzed on 2006-12-29
I'm very very new to ubuntu and linux as a whole.

When in run this command in terminal: sudo apt-get install msttcorefonts

I get to a confirmation notice, I type "y" and then hit enter.

I then get an error:

Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy/3v1n0 flashplayer-nonfree 9.0.21.78.2ubuntu2+3v1ubuntu1
  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78.2ubuntu2+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78.2ubuntu2+3v1ubuntu1_i386.deb)  The HTTP server sent an invalid reply header
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What's up with that?  Why is installing a set of fonts so hard?  I've been working on this for 8 hours and am getting VERY frustrated.

---

### Post by Manzabar on 2006-12-30
> **frotzed said:**
> What's up with that?  Why is installing a set of fonts so hard?  I've been working on this for 8 hours and am getting VERY frustrated.

1. You're working with a 3rd party repository which appears to be broken.
2. You've got other non-font packages that do not appear to be installed correctly (e.g. flashplayer-nonfree sounds like it's broken).  Apt (the cli utility behind Synaptic) is trying to automatically fix the broken packages; however since it's looking at a repository that is itself broken you kind of trapped.  If you go back to [my reply on your other post]("http://ubuntuforums.org/showthread.php?p=1947476#post1947476"), we may be able to get your issues fixed.

---

### Post by frotzed on 2006-12-31
I got it all worked out, Manzabar!  I'm so incredibly happy!  Ubuntu rocks!

---

### Post by puresniper on 2007-01-01
I get a 404 when I try to download the XML file, is there a mirror for it? I would love to get this working.

---

### Post by Fajer on 2007-01-01
Yes, I got the error when trying to get xml file and msfonts.tbz package. Anyone could host it somewhere and put the link here? or send it via email?

Please?

---

### Post by frotzed on 2007-01-01
> **Fajer said:**
> Yes, I got the error when trying to get xml file and msfonts.tbz package. Anyone could host it somewhere and put the link here? or send it via email?

Please?

[clicky](http://openswitch.org/backpack/myfonts.tar.gz) 8)

---

### Post by Fajer on 2007-01-01
Thanks a lot! :D

---

### Post by mastergunner on 2007-01-01
How do you enable the extra repositories? Also how do you exactly do it? I am a newb so step by step method is best for me. Thanks.

---

### Post by frotzed on 2007-01-02
System>Administration>Synaptic Package Manager>Settings>Repositories

---

### Post by mastergunner on 2007-01-02
Thanks frotzed. Could someone explain step bu step on how to install these fonts. Thanks.

---

### Post by frotzed on 2007-01-02
Install [Automatix](http://www.getautomatix.com/).  It's the easiest way to install the fonts.

---

### Post by mastergunner on 2007-01-02
Ftotzed I forgot  I was using Kubuntu so a little lost on how to configure repositories in it

---

### Post by frotzed on 2007-01-02
Sorry, I have no knowledge whatsoever of Kubuntu :(

---

### Post by bodhi.zazen on 2007-01-02
> **mastergunner said:**
> Ftotzed I forgot  I was using Kubuntu so a little lost on how to configure repositories in it

Same as Ubuntu :p

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by mastergunner on 2007-01-03
Thanks bodhi but Kubuntu doenst have a Synaptic Package Manager link. So anyone working Kubuntu if you can help me out with getting MS fonts on my computer I would appreciate it.

---

### Post by greygoo on 2007-01-03
> **puresniper said:**
> I get a 404 when I try to download the XML file, is there a mirror for it? I would love to get this working.

Don't know if it is the same file....but I found this to solve the problem: [http://www.auriance.com/docs/pcbsd/fonts/fontconfig/](http://www.auriance.com/docs/pcbsd/fonts/fontconfig/)

And I must say: I can see clearly now.... :D 

Now fonts in browser and in terminal-windows are how I like it best...
I just copied the files to /etc/fonts (after making a bak of my fonts.conf and installing the fonts) restartet x and felt better.

---

### Post by gh0st on 2007-01-03
This is really cool, thanks a lot. Now viewing some websites in Firefox doesn't look like they were designed by a 2 year old. Much appreciated :)

---

### Post by yopnono on 2007-01-03
Removed The Link.

---

### Post by mastergunner on 2007-01-03
Yopnono could you tell me how I am supposed to install these fonts? I have Kubuntu 6.06. Thanks and yes I have dowloaded the file and extracted it with Ark I think. It says it wants to open an external viewer or something.

---

### Post by mastergunner on 2007-01-03
Well I finally clicked on the file and it said it tried to download but could not get a hold of the site.

---

### Post by yopnono on 2007-01-04
> **mastergunner said:**
> Well I finally clicked on the file and it said it tried to download but could not get a hold of the site.

It's deb in side the archive. Extract it and install like normal. then if needed open the system settings for font and adjust the fonts.

---

### Post by elreteipos on 2007-01-04
I get this error:> pdedecker@BETAubuntu:~/Desktop$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Uitgestelde afbreking na eerdere fouten

---

### Post by kingtsy on 2007-01-05
i got an error message

ar: fontconfig.tbz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
please help

---

### Post by BeauX1 on 2007-01-07
> **yopnono said:**
> I will put the whole lot on my site. MS core font + config files all in a deb for installation to all the right places.
Including Tahoma

Hope the download speed is ok.
[http://www.mobelforum.com/download/msttcorefonts_nicefonts_1.4-1.tar.gz](http://www.mobelforum.com/download/msttcorefonts_nicefonts_1.4-1.tar.gz)
Thanks, that worked great.

---

### Post by Manzabar on 2007-01-07
> **mastergunner said:**
> Thanks bodhi but Kubuntu doenst have a Synaptic Package Manager link. So anyone working Kubuntu if you can help me out with getting MS fonts on my computer I would appreciate it.

Kubuntu uses Adept instead of Synaptic.  Look under Kmenu > System > Adept Package Manager.

---

### Post by calande on 2007-01-07
Sorry about that guys, I fixed the broken links in my original post ;)

> **puresniper said:**
> I get a 404 when I try to download the XML file, is there a mirror for it? I would love to get this working.

---

### Post by graficus on 2007-01-08
**yopnono** I appreciate your effort in posting the file.
how do I uninstall this "nice font" thing, it seems to have overwritten all settings without making backup. now i feel like am stuck in windows 95 look forever.

---

### Post by calande on 2007-01-09
Sorry about that. The screenshot was an extra warning to remind you how it was gonna look like in case you don't use Windows somewhere else :rolleyes:

Just remove /etc/fonts/local.conf

---

### Post by yopnono on 2007-01-09
> **graficus said:**
> **yopnono** I appreciate your effort in posting the file.
how do I uninstall this "nice font" thing, it seems to have overwritten all settings without making backup. now i feel like am stuck in windows 95 look forever.

Open synaptic and uninstall it.

---

### Post by calande on 2007-01-09
Ah ah!! Only if he used the .deb file that was posted above.

---

### Post by yopnono on 2007-01-09
> **calande said:**
> Ah ah!! Only if he used the .deb file that was posted above.

If you like I can remove the .DEB, now when you have fixed the links for you files.

---

### Post by SilBex on 2007-01-09
I installed the .deb from yopnono and now the Font looks generally good! Good Work guys!

Only if the Font is bold, it doesn't looks so good...  here an example:

[IMG]http://img481.imageshack.us/img481/4635/boldfontnq0.png[/IMG]

However its not so important. 

GreetZ!

---

### Post by graficus on 2007-01-09
you know what, i just found a solution. the hell with all this linux cr*p, and the fonts, and the command line, and the pain of doing anything with it. spent 99% of the time trying to make something work. how about work itself? sc*ew it. will stick with xp for now, and will get a mac a bit later. yeah, roll ur eyes, another whiner.
peace to u all.

---

### Post by yopnono on 2007-01-10
> **graficus said:**
> you know what, i just found a solution. the hell with all this linux cr*p, and the fonts, and the command line, and the pain of doing anything with it. spent 99% of the time trying to make something work. how about work itself? sc*ew it. will stick with xp for now, and will get a mac a bit later. yeah, roll ur eyes, another whiner.
peace to u all.

Linux is not for every one, specially if the user don't have the time to learn.
I guess the MS windows, did work directly first time you ever tried it, and your way.

Better luck next time :)

---

### Post by blueven on 2007-01-10
hi, thank you for your support!
i have installed the fontconfig of the first post, but firefox and openoffice do not appear with the new fonts, while the other programs yes.
Can you tell me what parameter i must set in firefox and openoffice to look they good?Anyone use Kubuntu?
I see that only kde application are ok, while all the other use the old fonts.

I use Kubuntu 6.10 , and i have installed so :
# sudo  apt-get install msttcorefonts
# sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

thank you for any answer...

---

### Post by Michaelt74 on 2007-01-10
Thanks for the thread, my desktop looks a little better with the new fonts.

I have a problem with Open Office fonts. I checked through the posts on this thread but none of the solutions helped (p10).

I have installed the MS core fonts and have the option to select Arrial and Times New Roman  
when I use OO, but no matter what I do the fonts look terrible in OO.

I downloaded Micrsoftfonts from pbiDIR - do I need to install these into some OO directory?

[http://www.pbidir.com/search.php?str=microsoft+fonts](http://www.pbidir.com/search.php?str=microsoft+fonts)

Which of these do I need?

If so please could someone tell me the install commands, step by step as I'm still a very Newbie

Thanks!

---

### Post by yopnono on 2007-01-11
> **Michaelt74 said:**
> 
I have a problem with Open Office fonts. I checked through the posts on this thread but none  
when I use OO, but no matter what I do the fonts look terrible in OO.
Thanks!

The Ubuntu OOo don't render system font well, the official does.

---

### Post by yopnono on 2007-01-11
> **blueven said:**
> hi, thank you for your support!
i have installed the fontconfig of the first post, but firefox and openoffice do not appear with the new fonts, while the other programs yes.
Can you tell me what parameter i must set in firefox and openoffice to look they good?Anyone use Kubuntu?
I see that only kde application are ok, while all the other use the old fonts.

I use Kubuntu 6.10 , and i have installed so :
# sudo  apt-get install msttcorefonts
# sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

thank you for any answer...

Open the system settings for fonts, then change the font setting for fx also set the font to use 96dpi and try different advanced (I think it called) settings for fonts. I'm on gnome.

---

### Post by blueven on 2007-01-11
i force to 96dpi but is the same! i see that in my system font setting in kde control is all set to sans serif 9. It's correct?
what settings do you have in firefox font and colors ' tab ?
is there anyone tha use kde ?

Help me please...

---

### Post by yopnono on 2007-01-11
> **blueven said:**
> i force to 96dpi but is the same! i see that in my system font setting in kde control is all set to sans serif 9. It's correct?
what settings do you have in firefox font and colors ' tab ?
is there anyone tha use kde ?

Help me please...

Ook I'm on kde now I don't  change anything in FX, my setting in kde are...
TT Fonts
sans serif 10
Use anti-alising > use sub pixel hinting RGB
96 DPI
-----
GTK styles and fonts
Use my KDE style

And all this is standard (more and less) :)

---

### Post by blueven on 2007-01-11
are your fonts working in Firefox and kde?
i try to reinstal fx but is the same!
Where you look for font settings in kde?

---

### Post by yopnono on 2007-01-12
> **blueven said:**
> are your fonts working in Firefox and kde?
i try to reinstal fx but is the same!
Where you look for font settings in kde?

K-menu > System settings > apperance / Fonts / GTK styles and fonts

There is no need to adjust any font settings in Firefox. Only in KDE

---

### Post by stormyuk on 2007-01-14
Hi, 

Thanks for the tips, I have a little problem in firefox and openoffice, firefox content is usually ok but with some buttons messed up and the menu bar etc is still as was before, OpenOffice has really BAD menu's and blurry content.

Any idea how to fix it?

Firefox:

[[IMG]http://img408.imageshack.us/img408/7610/snapshot3at8.th.png[/IMG]](http://img408.imageshack.us/my.php?image=snapshot3at8.png)
Thanks,

OpenOffice:

[[IMG]http://img408.imageshack.us/img408/8893/snapshot4gp8.th.png[/IMG]](http://img408.imageshack.us/my.php?image=snapshot4gp8.png)

Mike

---

### Post by blueven on 2007-01-14
> **yopnono said:**
> K-menu > System settings > apperance / Fonts / GTK styles and fonts

There is no need to adjust any font settings in Firefox. Only in KDE


Thank you very much!!!
I haven't set the kde fonts for gtk application!!!

Now is OK!!!

---

### Post by stormyuk on 2007-01-14
> **yopnono said:**
> K-menu > System settings > apperance / Fonts / GTK styles and fonts

There is no need to adjust any font settings in Firefox. Only in KDE

Ahh that worked for me too in firefox. Thanks very much. OpenOffice is still a bit messed up compared to everything else though.

Edit: Also some websites, usually linux resources :) seem to override the setting and force anti-aliased fonts? Take a look at this one:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

[[IMG]http://img123.imageshack.us/img123/4493/snapshot7rm4.th.png[/IMG]](http://img123.imageshack.us/my.php?image=snapshot7rm4.png)

Compare that to the clean lines in Windows XP

[[IMG]http://img158.imageshack.us/img158/8177/image1dm7.th.png[/IMG]](http://img158.imageshack.us/my.php?image=image1dm7.png)

Disapointing :(

I have been playing more and still can't get to the bottom of this, I am finding more and more webpages that just look odd in ubuntu/linux compared to XP using Firefox. All I want is my ubuntu Firefox to look like XP. How hard can it be? :( 

I even tried de-checking the "allow web pages to select fonts" option but that really messes is up.  Is there a way I can select the "exact" same fonts in Firefox's font options as that in windows? (Arial, Times New Roman etc etc). I am at work at the moment so can't check what font options Firefox gives me in Ubuntu. Will that just mess it up more?

Thanks for any assistance you can provide. If I could bottom this I would be one step closer to ditching XP.

Mike

---

### Post by Zdravko on 2007-01-14
I have a problem... The MS fonts were installed. Then I extracted the font-config - OK. The fonts now really look sharper. But can someone tell me the best settings for them? Including the general font for Ubuntu and the Firefox settings for it? Because I use Serif 10pt by default and it is really sharp for my eyes.

---

### Post by stormyuk on 2007-01-15
While still not 100% perfect I have managed to get is very very close by selecting the same fonts in Linux Firefox preferences to that of Windows XP firefox, some fonts STILL refuse to show without aliasing but its a lot better than it was.

Cheers,

Mike

---

### Post by augie0x on 2007-01-16
Running sudo apt-get update && sudo apt-get upgrade from time to time helps in installing everything u need without any errors!

---

### Post by blueven on 2007-01-18
But it's possible to install the MS Sans Serif and the MS Serif too?

---

### Post by John Bennett on 2007-01-21
I use Firefox to read long articles.

This is soooo much better.

Obrigado Calande meu amigo !

---

### Post by Jarn on 2007-01-29
Is there any way to change what programs use these modified fonts? I love it in Konqueror, but I absolutely LOATHE it in a terminal. If it can't be set on a program by program basis, how do I change it back to the way it was originally?

---

### Post by Derspankster on 2007-02-02
I likes it better the way it was. I had installed TT fonts but hadn't configured them. They looked better that way than they do now. Any way to revert back to what I had?

---

### Post by linuks on 2007-02-02
> **BeauX1 said:**
> Thanks, that worked great.

Yopnono,

For me too, It worked beautifully.

---

### Post by kanha on 2007-02-15
superb:guitar:

---

### Post by calande on 2007-02-15
> **stormyuk said:**
> Edit: Also some websites, usually linux resources :) seem to override the setting and force anti-aliased fonts? Take a look at this one:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

[[IMG]http://img123.imageshack.us/img123/4493/snapshot7rm4.th.png[/IMG]](http://img123.imageshack.us/my.php?image=snapshot7rm4.png)

Compare that to the clean lines in Windows XP

[[IMG]http://img158.imageshack.us/img158/8177/image1dm7.th.png[/IMG]](http://img158.imageshack.us/my.php?image=image1dm7.png)

Disapointing :(

Yes, this happens because these guys force crappy fonts (Bitstream family) to Unix users, because they know they have Bitstream installed, while Windows doesn't. The only way is to solve this problem is to uninstall the Bitstream crap :)

---

### Post by zemitras on 2007-03-12
Hi there! 

I have been struggling with the installation of msttcorefonts for a wile, I followed your guide (extracting files) and nothing happened :( 

When I do "apt-get install msttcorefonts" I get error, same error in automatix2:

```
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I really don't know what to do, can anybody help me?

I have ubuntu 6.10 Edgy

Regards

---

### Post by sagara on 2007-03-17
[COLOR="Silver"]The link in the original post for the config file is broken **again**... Could someone fix it or post a new link please?  Thanks.[/COLOR]

Nevermind... link worked on the 5th try.

---

### Post by sagara on 2007-03-18
Hi I followed your steps and it worked nicely! thanks!

However I am getting the following **mild error** whenever i run **gedit** from the terminal:

```
$ gedit file
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

```
This however doesnt stop gedit from running.

The contents of my ~/.fonts.conf file is:
```
<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

What seems to be the problem?
Thanks in advance!

---

### Post by joebloggs on 2007-03-24
The code has incorrectly formed quotation marks.

They are itallicised and therefore not recognised. Open the file and retype your double quotes to make them regular ones. Alternatively replace them with a single ' 

Joe

---

### Post by sagara on 2007-03-24
> **joebloggs said:**
> The code has incorrectly formed quotation marks.

They are itallicised and therefore not recognised. Open the file and retype your double quotes to make them regular ones. Alternatively replace them with a single ' 

Joe

Joe, that did the trick.  Thanks a lot!

---

### Post by attorianzo on 2007-04-14
It worked perfectly but... Now I want standard gnome fonts again!! What I have to do??

---

### Post by calande on 2007-04-14
Rename /etc/fonts/local.conf to local.conf.bkp

---

### Post by attorianzo on 2007-04-14
> **calande said:**
> Rename /etc/fonts/local.conf to local.conf.bkp
Worked :) thank you.

I suggest you to add it to your guide (thank you great guide!)

---

### Post by stormyuk on 2007-04-17
> **calande said:**
> Yes, this happens because these guys force crappy fonts (Bitstream family) to Unix users, because they know they have Bitstream installed, while Windows doesn't. The only way is to solve this problem is to uninstall the Bitstream crap :)

How? :D

Thanks,

Mike

---

### Post by yopnono on 2007-04-17
> **stormyuk said:**
> How? :D

Thanks,

Mike

Or you can set the firefox to use the font * sans-serif * as default. Make sure the fonts ar set just like the pic.
That works for me.

See img.

---

### Post by gustavo :) on 2007-04-17
Nice tutorial :) worked well here (using Kubuntu), now my fonts are looking good for me...
But I've got a little issue...I can't set my Window Title font when using Beryl :S
The font that i've set appears when I'm using KWin window manager, but when I change to beryl the Window Title font turns to Tahoma :\

What can I do?

thx

---

### Post by CarpKing on 2007-04-19
> **gustavo :) said:**
> Nice tutorial :) worked well here (using Kubuntu), now my fonts are looking good for me...
But I've got a little issue...I can't set my Window Title font when using Beryl :S
The font that i've set appears when I'm using KWin window manager, but when I change to beryl the Window Title font turns to Tahoma :\

What can I do?

thx

Launch Emerald Theme Manager and go to the Edit Theme tab, then the Titlebar tab.  On the left side should be an option called "Title-Text Font."

---

### Post by finferflu on 2007-04-20
Is there any way to revert this to the original? Now my fonts are all ultra-thin and not stylish at all, I liked it more before... shall I just delete the files I have copied in /ect/fonts/ ?

Thanks

---

### Post by Jarn on 2007-04-20
That's what I did when I wanted to revert and it seemed to work.

---

### Post by finferflu on 2007-04-20
> **Jarn said:**
> That's what I did when I wanted to revert and it seemed to work.
Thanks! that worked as a charm :)

---

### Post by Yggdrasill on 2007-04-23
Is there a way to apply these font effects to Konqueror?

---

### Post by TravisNewman on 2007-04-23
Everything was smooth and looked VERY nice, except for the forums. When I came here it was just unreadable. So I just deleted those conf files and I'm back to normal. I don't know why it did that just to the forums.

---

### Post by calande on 2007-04-23
> **Yggdrasill said:**
> Is there a way to apply these font effects to Konqueror?

Make sure you use generic font families in Konqueror (Sans Serif, Serif, Monospace, etc...)

---

### Post by navneeth on 2007-04-23
This method doesn't seem to work for me in Feisty. I had no problems with it in Edgy. But here, after at least a couple of logins, I don't see the fonts. 

```
navneeth@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
navneeth@ubuntu:/etc/fonts$ ls
alias.conf  conf.d      fonts.dtd   misc.conf
conf.avail  fonts.conf  local.conf  msfonts-rules.conf

```

---

### Post by navneeth on 2007-04-24
Anyone?

---

### Post by yopnono on 2007-04-24
Removed The Link.

---

### Post by calande on 2007-04-24
Could you make sure the fonts are still in the fonts directory where they were extracted?

Could you make sure the fonts directory is listed in xorg.conf also?

Are you able to use the fonts in other applications such as OpenOffice.org or Abiword?

---

### Post by navneeth on 2007-04-24
> **calande said:**
> Could you make sure the fonts are still in the fonts directory where they were extracted?
Now I don't even find a TTF directory at the address provided in the first post! :confused: 
```
navneeth@ubuntu:/usr/X11R6/lib/X11/fonts$ ls
encodings

```

I tried extracting the msfonts.tbz, but I get an error
```
navneeth@ubuntu:~$ sudo tar xvjpf Desktop/msfonts.tbz -C /usr/X11R6/lib/X11/fonts/TTF/
tar: /usr/X11R6/lib/X11/fonts/TTF: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

```


> Are you able to use the fonts in other applications such as OpenOffice.org or Abiword?
I didn't find those fonts listed in OO. 

yopnono,
 Thanks for the file. I'll give it a try if this doesn't work out.

---

### Post by calande on 2007-04-24
Strange... Type the following:

```
%sudo mkdir -p /usr/X11R6/lib/X11/fonts/TTF
```

Then start over: [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
Did it work now?

---

### Post by navneeth on 2007-04-27
> **calande said:**
> Strange... Type the following:

```
%sudo mkdir -p /usr/X11R6/lib/X11/fonts/TTF
```

Then start over: [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
Did it work now?

Sorry for the delayed reply. I'm afraid that the above method didn't work. The TTF folder was created with the fonts, but somehow that config file didn't do its magic. :( Surprisingly, I find Opera displays MS fonts, even after deleting the TTF files.

---

### Post by chefare on 2007-04-30
> **navneeth said:**
> Sorry for the delayed reply. I'm afraid that the above method didn't work. The TTF folder was created with the fonts, but somehow that config file didn't do its magic. :( Surprisingly, I find Opera displays MS fonts, even after deleting the TTF files.

I tried to install the Microsoft fonts on my Ubuntu 7.04, but I hade the same problem (the directory TTF was not present), so I created it and reinstalled fonts, but... it doesn't go, I don't see the new fonts :-(
I remember that few days ago I tried to install Microsoft fonts on Ubuntu 7.04 upgraded with KDE interface (Kubuntu-desktop) and I saw and used fonts (I don't know if this is the reason)... but Kubuntu was instable and I reinstalled normal Ubuntu... I hate the original fonts of Ubuntu, is there a way to use Microsoft fonts on Ubuntu too? :-(

---

### Post by yopnono on 2007-05-01
> **calande said:**
> Strange... Type the following:

```
%sudo mkdir -p /usr/X11R6/lib/X11/fonts/TTF
```

Then start over: [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
Did it work now?

Calande is there any specific reason why you want to have the fonts in that dir?
The *normal* location is ```
/usr/share/fonts/truetype
``` there is where I always put the fonts.
And so far I have not had any problems.

---

### Post by calande on 2007-05-01
Try it. Maybe the fonts dir changed with newer versions of Debian or X.org? It used to be /etc/fonts/<some_dir>

Who know, maybe it'll just work! :)
Please let us know.

---

### Post by yopnono on 2007-05-01
> **calande said:**
> Try it. Maybe the fonts dir changed with newer versions of Debian or X.org? It used to be /etc/fonts/<some_dir>

Who know, maybe it'll just work! :)
Please let us know.

```
/etc/fonts/
```
Is that not only for the font config files?

---

### Post by Braese on 2007-05-02
How can i enable ClearType for this Solution? Thx

---

### Post by sv87411 on 2007-05-02
I have tested this on Feisty and can confirm that you need to put the fonts in

```
 /usr/share/fonts/truetype
```

So for Feisty users, follow the original instructions, but extract the fonts using the following command:

```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```

It's worked for me and I now have nice MS fonts. :)

---

### Post by NilsE on 2007-05-03
> **Braese said:**
> How can i enable ClearType for this Solution? Thx
I think the closest to ClearType option you will get is to go into font preferences and click on details and tinker with the hinting and smoothing options.

---

### Post by Ruhe on 2007-05-05
Hi, I have a problem:

[[IMG]http://img508.imageshack.us/img508/5202/screenshotng2.th.png[/IMG]](http://img508.imageshack.us/my.php?image=screenshotng2.png)

I followed the first post in this thread, I tried to install deb file, but still many apps don't want to use sharp fonts. It's not a problam of russian lang, I logged in with english language, but it did't change anything.

I think that this can be my problem(wrong dpi and length&height in mm):
```
ruhe@desktop:~$ xdpyinfo | grep dimensions
  dimensions:    1024x768 pixels (**321x241** millimeters)
ruhe@desktop:~$ xdpyinfo | grep resolution
  resolution:   ** 81x81** dots per inch
```

I used this line in xorg.conf
```
DisplaySize    270    203    # 1024x768 96dpi
```
but it doesn't take effect. I don't know what to do (((

---

### Post by calande on 2007-05-05
Make sure in the Gnome front-end you're using generic font families (Sans Serif, Serif, Monospace...) instead of Bistream or Dejavu.

---

### Post by Ruhe on 2007-05-06
On my screenshot I had Tahoma font in all settings excluding monospace. 
Now I changed font to sans(tried serif), but still no changes. It seems that there is another config file which blocks settings from Font Manager. A lot of apps(firefox, opera, firestarter) use sharp fonts but others don't.

---

### Post by smdeep on 2007-05-12
Works perfectly for me in Feisty, had worked perfectly in Kubuntu Edgy. The man is a genius and this should be  a sticky IMHO.
:)

---

### Post by calande on 2007-05-12
No, not a genius, but it took a fair amount of time due to sparse documentation.
Namaste,

---

### Post by adarkenigma on 2007-05-13
how can revert back to original setting?

---

### Post by yopnono on 2007-05-13
> **adarkenigma said:**
> how can revert back to original setting?

Humm let's see. Ah, just remove the files you added to your system ;)

---

### Post by adarkenigma on 2007-05-13
okay thanks let me try that

---

### Post by calande on 2007-05-13
Or just rename local.conf to local_.conf

:)

---

### Post by ryanVickers on 2007-05-28
wow, those are awful! - perfect, just like windows! :p

---

### Post by calande on 2007-05-29
If it's to add a flaming comment meaning in a nutshell that all that is from Microsoft "is evil", no thanks. Respect our choice please :evil:

---

### Post by gozalo on 2007-05-29
hmmmmmm 

It's not working for me :-(

can u check here plz :o

[http://ubuntuforums.org/showthread.php?t=456881&page=1](http://ubuntuforums.org/showthread.php?t=456881&page=1)

---

### Post by michaelzap on 2007-06-02
Hmm. I really don't like how it looked after I did this, and just uninstalling the font package made my system a bunch of gobbledygook that was hard to reset to something readable. So how can I get my old fonts back and undo those XML files please?

---

### Post by calande on 2007-06-02
Remove /etc/fonts/local.conf. If you had had a look at the original screenshot beforehand, you wouldn't have done this mistake.

---

### Post by michaelzap on 2007-06-02
Thanks. That did the trick. I was afraid to just delete it after how totally freaked it it was when I only removed the  m$ fonts...

---

### Post by Delacroix on 2007-06-05
Can anyone host the new fontconfig file that was in the PC-BSD Forum?

[http://www.auriance.com/docs/fonts/fontconfig.tbz](http://www.auriance.com/docs/fonts/fontconfig.tbz) This link is dead. Or is this the same as the one on page 1?

EDIT: Is it just me or are the fonts hurting people's eyes now? I can't stand the fonts now damn. Now I'm back on XP with Cleartype on and it so much better and sharper unlike the blurry fonts on Ubuntu.

---

### Post by Arseny on 2007-06-06
calande, I need your help. How can I add Lucida Console font to this kit? I would like to use it with Konsole and Kate :/ Thx :)

---

### Post by dannymichel on 2007-06-09
I don't like the way it displays fonts in firefox. Is there any way I can undo it for Firefox?

---

### Post by dannymichel on 2007-06-09
Is there any way to undo this ONLY for Firefox?
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!--  PC-BSD - Fonts configurations v.12012006-->

<!-- Miscellaneous settings -->

<include ignore_missing="yes">misc.conf</include>

<!-- Define alias -->

<include ignore_missing="yes">alias.conf</include>

<!-- Rules for Microsoft fonts -->

<include ignore_missing="yes">msfonts-rules.conf</include>


</fontconfig>
```

---

### Post by calande on 2007-06-09
Arseny: Just add Lucida to your fonts directory, log out and log back in.

Danny: Yes, you can do it due to a bug! :) Open msfonts-rules.conf and remove the lines that contain the word "pixelsize", log out and log back in. It will blur fonts out in Firefox :)

---

### Post by Nephiel on 2007-06-13
> **TheMono said:**
> This seems to have caused quite an issue - it's hard to explain this, but now my computer is rendering only the left hand side of each line, until I select it, and upon selection, it fixes itself.

For example, if I bring up a menu, go to the "sound and video" section, I can see "GXine" in the menu. If I then run my mouse over that (ie, without clicking, just making the background go dark - what do you call doing that lol), it changes then to "GXine Movie Player" - ie, it renders the full string of text.

Ideas? I do much prefer the fonts like this and I'd like to keep it if I can get rid of this problem.

Oh, and also, it happens in almost everything - the GKSudo dialogbox, in Evolution, etc.

I have the same issue, but it seems to happen only in Firefox. I've noticed that it happens when browsing a page using MS fonts without antialiasing and with the CSS attribute "letter-spacing:" applied to them, but it could happen in other situations as well. When I'm not using MS fonts without antialiasing, the text is correctly displayed.

On these web pages, on some lines of text, Firefox shows only the first word of each line until I "touch" the rest of the line. Let me explain:

For example, one page which shows this bug is [this one](http://samurai1200.blogspot.com/2006/12/be-asteroid.html).
I have nothing to do with that page BTW, it's just the first page I bookmarked which showed this bug.

In that page, there's a line of text like this:
```
Saturday, December 02, 2006
```
Firefox only shows this:
```
Saturday,
```
until I click to select the rest of the text with the mouse, making it visible. I know the "invisible" text is there because the mouse cursor changes from the little arrow to the text caret when I move it over the text; it's just that the text can't be seen.
However, in that same page, there's another line of text like this:
```
View my complete profile
```
Only the first word "View" is shown. But unlike the other line, this one happens to be a link, and so when I hover the mouse over the text, the link text changes color and gets underlined. When this happens, the entire line of text becomes visible.

All this is a bit hard to explain. I'm attaching screenshots so you can see better what I'm talking about, but if you try it for yourselves, the better. There are quite a few lines like those in that page.

I want to use MS fonts without antialiasing because I need web pages to be shown just like they would under Windows, or as similarly as possible. Basically I want MS fonts for web browsing.

---

### Post by metjay on 2007-06-18
Thanks dude, 
you just saved  my life.
works fine

---

### Post by Luis Marks on 2007-06-21
Hey, thanks for your great work. I use Tahoma font size 8 but in small and italic fonts this view ugly (snapshot of K3B attached). How can i make this better ?

PS: Sorry for the bad english...

---

### Post by calande on 2007-06-21
Infelizmente, there's nothing you can do about it. I talked a few months ago with the Freetype devs and they said they were working on it always, but it's a complicated algorythm... It's improving very slowing across new versions. You shouldn't use a fonts that small IMO. The font size you're using for the rest of your applications is perfect, I think :)

---

### Post by Luis Marks on 2007-06-21
You are quickly :D . Yes, all the applications is perfect ! Thanks for the answer and for the great work. ;)

---

### Post by FooFoo_2 on 2007-06-22
Hi everyone

I found a link on this tutorial on a french board. I followed the procedure and all is working, except one small detail that I could not solve. I hope that you can help me.

After installing and applying the new fonts on my system, I just remarked that the passwords fields (aMuleGUI, Firefox master password, etc) were filled with stars (*) and no more with circles. And I can find any configuration file where I can specify if I want to use stars (*) or circles. Before applying the new fonts, the password fields were filled with circles.

An interesting thing is that the passwords fields of GDM and gksudo are filled with circles (before and after applying the new fonts).

Here a printscreen of aMuleGUI:
[[IMG]http://img404.imageshack.us/img404/3166/connectmr2.th.png[/IMG]](http://img404.imageshack.us/my.php?image=connectmr2.png)

Thank you in advance for your help and have a nice day.

Best regards from Switzerland :)

---

### Post by sambehera on 2007-06-22
thanks... this worked... much better than truning off anti-aliasing uptil "pt 9"... 

i had followed the howto here... [http://alkalay.net/linux/docs/font-howto/Font.html]("http://alkalay.net/linux/docs/font-howto/Font.html")

but that only worked well for the root account... the font rendering in my usual account actually became worse (monochromatic type) ... 

this did fix my problem but added the stars in the password field... and anti aliasing doesnt work for my "trebuchet 10pt" titlebar font anymore ... now am looking to smooth out the fonts in swiftweasel.. hope the method described above works...

overall... thanks...!! i was really baffled why the earlier fix was working for my root user account but not for my usual one..:D

---

### Post by turezky on 2007-06-28
That was the last post convincing me (in addition to some malware on my vista) to switch completely to ubuntu :) Thank you, thank you, thank you :)

---

### Post by Sabretooth on 2007-07-15
Hi, I love this fix. It makes Ubuntu's fonts so much nicer! But I have one rather obtrusive problem.

My fonts aren't anti-aliased, as far as I can tell, especially at the italics. This is really bugging me, because I'm used to smooth, cleartype-esque fonts. How do I make them smooth?

---

### Post by calande on 2007-07-15
Namaste, this is the way they're supposed to look like, just like the [screenshot of the first post]("http://ubuntuforums.org/showthread.php?t=208396") :)
If you dislike, rename the /etc/fonts/local.conf file to /etc/fonts/local.conf.bkp ;)

---

### Post by Pronco on 2007-07-15
Tahoma font doesn't work properly. It looks like a squares 

Does it work with somebody ?

Cheers,
Pronco

---

### Post by Sabretooth on 2007-07-16
Well, yeah but in your screenshot, things are much smoother. There is some jaggedness, but I wouldn't mind that. My fonts are looking rather rough. Can you tell me a way to anti-alias/smoothen fonts without affecting this fix? :(

@Pronco: My Tahoma's working perfectly well. Except for the aforementioned problem. :D

---

### Post by srg84 on 2007-07-27
Thanks is perfect.

---

### Post by seelk on 2007-08-01
Worked like a charm under Kubuntu Feisty.  Question, would this work on other distros like Gentoo, Fedora, etc.?

---

### Post by calande on 2007-08-02
Yes, it works on any Linux/*BSD distro ;)

---

### Post by ferd on 2007-08-07
> **calande said:**
> I tweaked the fontconfig XML files so that fonts look like on Windows. This code is borrowed from [PC-BSD](http://www.pcbsd.org). First, let's install the Microsoft fonts. You have 2 ways of doing so:

Either download the [fonts](http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz) into your home directory and install them on your system:

```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```

Or, enable non-free, universe and multiverse repositories and install the Microsoft fonts:

```
sudo apt-get install msttcorefonts
```

You now have the Microsoft fonts installed. Let's configure your system now.

Download the [xml files]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz") and extract the file into /etc/fonts/ as root:

```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

Log out from Ubuntu and relog in. Here's how your desktop will look like:

[[IMG]http://img412.imageshack.us/img412/6972/ubuntu5ui.th.png[/IMG]](http://img412.imageshack.us/img412/6972/ubuntu5ui.png)

It's a lot more complex than disabling antialiasing at small font sizes :)

[SIZE="4"][DIGG IT!]("http://digg.com/linux_unix/Display_Microsoft_fonts_in_Unix_like_on_Windows")[/SIZE]

Thank you so much for this. Excellent on my multisync 90 GX2.

---

### Post by taisao on 2007-08-16
looks quite like windows xp without cleartype turning on. 

Doesn't look good on my LCD :(

thanks for the Tahoma fonts :KS

---

### Post by calande on 2007-08-16
Just out of curiosity, could you provide us with a screenshot of your current desktop? :)

---

### Post by taisao on 2007-08-16
this is the way it looks with yours xml files:

[IMG]http://img.photobucket.com/albums/v292/WhyYouPickMyName/desktop/snapshot2.png[/IMG]


this is how I have it now (I like this more):

[IMG]http://img.photobucket.com/albums/v292/WhyYouPickMyName/desktop/snapshot1.png[/IMG]

---

### Post by calande on 2007-08-16
Yeah, they look better, but is this the default Kubuntu configuration? These fonts look more polished than on a standard install to me. Could you give more details if you tweaked your configuration?

---

### Post by taisao on 2007-08-16
I have read and tried many howto.

But I think this are the one that I get the result with:

Firefox Widgets - [http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596) 
Improved subpixel font rendering for Feisty - [http://ubuntuforums.org/showthread.php?t=343670&highlight=fonts](http://ubuntuforums.org/showthread.php?t=343670&highlight=fonts)
HOW TO: Improve Ubuntu font rendering.  - [http://ubuntuforums.org/showthread.php?t=515947](http://ubuntuforums.org/showthread.php?t=515947)

and this are the settings

[IMG]http://img.photobucket.com/albums/v292/WhyYouPickMyName/desktop/snapshot3.png[/IMG]

---

### Post by boob11 on 2007-08-16
Thank you

---

### Post by calande on 2007-08-16
Cool, well thanks for the tips, I have never used the Liberation fonts but they are clean on your screenshot, I'll try them this week-end ;)

---

### Post by daWsOn_s on 2007-09-20
Hi is there any possibilty to use this clear fonts only in the applications that require it? For example why if I use Sans Serif font as the default system font it applies Arial, why? I just want this font to display for example in firefox on a web site that use it in the CSS but still having my ubuntu default fonts. Thanks

---

### Post by calande on 2007-09-20
No. All applications use fontconfig these days, so if you change the configuration, it applies to all applications (almost).

---

### Post by daWsOn_s on 2007-09-21
Mmmm ok but why Arial? what file should I change to set another default font and how?

---

### Post by gladstone on 2007-09-21
Is it only me, or does Cleartype/Font Anti-aliasing/Smoothing whatever you want to call it look as bad as I think it does?

I really can't see the appeal of blurry fonts. Everyone say's it's designed for LCD's in mind, but I just can't get on with them on my laptop - perhaps it's my screen?

Anyway, running through this process (it's a shame I didn't find this thread to start with) was the first thing I did when installing Ubuntu - perhaps I'm being too hasty?

---

### Post by crjackson on 2007-09-23
> **calande said:**
> Ok, I think I know what the problem is. Go to your Firefox font configuration and select generic family fonts, for monospace you will select "Monospace" instead of what there is currently.

Okay, I can't find anything called "generic family fonts", what am I missing here?

---

### Post by RaviJ on 2007-09-29
Hi
  I got a problem with the fonts after installing. so i wanted to revert back as suggested in the 2nd page of this 27 pages long thread, but i couldnt. i'm denied permission. is there anyway in which i can undo my installation of these microsoft fonts on my ubuntu?
thanks a lot

---

### Post by taisao on 2007-09-29
> **RaviJ said:**
> Hi
  I got a problem with the fonts after installing. so i wanted to revert back as suggested in the 2nd page of this 27 pages long thread, but i couldnt. i'm denied permission. is there anyway in which i can undo my installation of these microsoft fonts on my ubuntu?
thanks a lot

if you want to delete it with nautilus then run nautilus as root, do so:

pressing: Alt+F2
type: gksudo nautilus
type: **** <- yours superuser password

and delete the files

---

### Post by RaviJ on 2007-10-01
Hi 
Thanks a lot. it helped. but the file is only 339bytes. i think the msfonts would be a lot because many files got installed during the installation process. by just deleting the small local.conf file would all the process be reversed?i

---

### Post by taisao on 2007-10-02
By deleting the local.conf you will get the fonts settings back like before, you still have the mscorefonts on yours system. That are just fonts file and you can just leave them like how they are.

---

### Post by Naatan on 2007-10-06
Thanks a lot mate! I really like the font smoothening in Ubuntu but it feels mighty refreshing to have the crispy windows font feeling back again, to be quite honest it's easier on the eyes

---

### Post by walkerk on 2007-10-07
Here's a script that'll complete this installation for Feisty or Gutsy...

Download and then...
```
cd /path/to/fonts.sh
```

Make it executable...
```
chmod +x fonts.sh
```

Run it...
```
./fonts.sh
```

I really prefer my fonts like this so I thought I'd contribute..

---

### Post by taisao on 2007-10-07
screenshots please?

---

### Post by walkerk on 2007-10-07
....

---

### Post by gladstone on 2007-10-08
Theres one on the first post here: [http://ubuntuforums.org/showpost.php?p=1209754&postcount=1](http://ubuntuforums.org/showpost.php?p=1209754&postcount=1)

---

### Post by taisao on 2007-10-08
> **gladstone said:**
> Theres one on the first post here: [http://ubuntuforums.org/showpost.php?p=1209754&postcount=1](http://ubuntuforums.org/showpost.php?p=1209754&postcount=1)

I mean a screenshot of walkerk desktop :KS

Thank you walkerk,

---

### Post by taisao on 2007-10-13
> **walkerk said:**
> Here's a script that'll complete this installation for Feisty or Gutsy...

Download and then...
```
cd /path/to/fonts.sh
```

Make it executable...
```
chmod +x fonts.sh
```

Run it...
```
./fonts.sh
```

I really prefer my fonts like this so I thought I'd contribute..

what change do I need to make if I want to enable sub-pixel hinting for those mscorefonts (cleartype in windows term)?

---

### Post by calande on 2007-10-13
> **taisao said:**
> what change do I need to make if I want to enable sub-pixel hinting for those mscorefonts (cleartype in windows term)?

You will want to comment out the line that defines the rules for the MS fonts: open /etc/fonts/local.conf and comment out this line from: ```
<include ignore_missing="yes">msfonts-rules.conf</include>
``` to: ```
<!--<include ignore_missing="yes">msfonts-rules.conf</include>-->
``` Or you can also rename msfonts-rules.conf to msfonts-rules.bkp.conf

Installing just the MS fonts without fontconfig would have had the same effect. Just enable sub-pixel hinting in your fonts control panel.

:)

---

### Post by taisao on 2007-10-13
> **calande said:**
> You will want to comment out the line that defines the rules for the MS fonts: open /etc/fonts/local.conf and comment out this line from: ```
<include ignore_missing="yes">msfonts-rules.conf</include>
``` to: ```
<!--<include ignore_missing="yes">msfonts-rules.conf</include>-->
``` Or you can also rename msfonts-rules.conf to msfonts-rules.bkp.conf

Installing just the MS fonts without fontconfig would have had the same effect. Just enable sub-pixel hinting in your fonts control panel.

:)

oh :)

I choose to comment that one line out. Thanks :KS

---

### Post by calande on 2007-10-13
You welcome. Could you show us how it looks like? Is it as good as ClearType?

---

### Post by taisao on 2007-10-13
uhm, maybe I like Cleartype better, I don't know, I don't use it anyway. Here you decide it:

WindowsXP firefox:
[http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/winxp_shot1.jpg](http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/winxp_shot1.jpg) (zoom 100%)
[http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/winxp_shot2.jpg](http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/winxp_shot2.jpg) (zoom 140%)

Ubuntu firefox:
[http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr7.png](http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr7.png) (zoom 100%)
[http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr6.png](http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr6.png) (zoom 140%)




And this is what I use at the moment, Ubuntu firefox & don't use pages fontfamily preference:
[http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr8.png](http://img.photobucket.com/albums/v292/WhyYouPickMyName/compTemp/sr8.png) (zoom 120%)



What do you think?

---

### Post by JohnOhl on 2007-10-13
I followed the tutorial to a T and I love the fonts how they are now.

I can't seem to get 'clearish-type' working on this feisty machine but as it is now it looks almost identical to a windows XP machine without cleartype enabled. Which is much, much better than the standard ubuntu fonts at small sizes.

[http://img134.imageshack.us/img134/5843/screenshotsx1.png](http://img134.imageshack.us/img134/5843/screenshotsx1.png)

---

### Post by xcafeus on 2007-10-16
awesome! thanks man.

---

### Post by mencho78 on 2007-10-19
I can't unpack the files in the fonts folder, it says I'm not the owner, and I don't know how to change permissions for root folders.... I'm running Gutsy

can anyone please help me? :confused:

---

### Post by NilsE on 2007-10-19
> **mencho78 said:**
> I can't unpack the files in the fonts folder, it says I'm not the owner, and I don't know how to change permissions for root folders.... I'm running Gutsy

can anyone please help me? :confused:
Go into a terminal and start Nautilus as root

gksudo nautilus

---

### Post by NilsE on 2007-10-19
> **JohnOhl said:**
> I followed the tutorial to a T and I love the fonts how they are now.

I can't seem to get 'clearish-type' working on this feisty machine but as it is now it looks almost identical to a windows XP machine without cleartype enabled. Which is much, much better than the standard ubuntu fonts at small sizes.

[http://img134.imageshack.us/img134/5843/screenshotsx1.png](http://img134.imageshack.us/img134/5843/screenshotsx1.png)
Go one more step in the font configuration and select the details page then select slight and close.  Do not change anything on the main preference screen.

I think you will be pleasantly surprised.

---

### Post by Zillion on 2007-10-19
> **walkerk said:**
> Here's a script that'll complete this installation for Feisty or Gutsy...

Download and then...
```
cd /path/to/fonts.sh
```

Make it executable...
```
chmod +x fonts.sh
```

Run it...
```
./fonts.sh
```

I really prefer my fonts like this so I thought I'd contribute..

Thanks.. very nice.

---

### Post by calande on 2007-10-19
Does it only return a warning message and unpack or doesn't it work at all? Are you logged as root or as user? You need to use "sudo".

---

### Post by MemoryDump on 2007-10-23
how can you tell if it's actually using the msfonts?
according to this screenshot I just took it seems to be the defaults to me.. and yes I did reboot :)

---

### Post by calande on 2007-10-23
Yes, these are the fonts (although the JPEG is so compressed that I can hardly see). Next time, please use PNG for your screenshots.

---

### Post by Scimu on 2007-10-31
Thanks a lot for this. I got it working first time! :D

---

### Post by cookies on 2007-10-31
Thanks for this tutorial!
I know this sounds insane, but can this be done for all fonts? Or, at least, this be the default setting? I have some fonts that still anit-alias for some reason.

---

### Post by calande on 2007-10-31
> **cookies said:**
> Thanks for this tutorial!
I know this sounds insane, but can this be done for all fonts? Or, at least, this be the default setting? I have some fonts that still anit-alias for some reason.

Yes, this is actually done for all Microsoft fonts. Could you show us a screenshot?

---

### Post by cookies on 2007-10-31
All my MS fonts do, but not certain fonts, which gets annoying in cases like this:

---

### Post by calande on 2007-10-31
There's nothing you can do in this case. The WINE web site is designed to use blurred fonts, unfortunately. Unless you're able to convince its webmaster to use sans-serif instead of Bitstream Vera Sans (which I doubt).

---

### Post by cookies on 2007-10-31
Blargh. Thanks for the info.

---

### Post by Dynych on 2007-11-01
> **walkerk said:**
> 
Run it...
```
./fonts.sh
```
The Italic fonts still anti-aliased. How to fix it?

---

### Post by tokinux on 2007-11-01
> **Dynych said:**
> The Italic fonts still anti-aliased. How to fix it?

Same problem here. Italic fonts are still AA'ed everywhere; system & browser

---

### Post by Dynych on 2007-11-01
Gutsy solve all my problems with fonts.:)

---

### Post by shaula on 2007-11-03
Hello All,

i did not managed to install msttcorefonts via all traditional methods due to an annoying error message.

i managed to install the MS-Win fonts by the use of kfontview (if you don't have it install it).

i initiated <sudo kfontview> from the terminal.
looked for the appropriate fonts in the windows drive (i have a dual boot XpPro-Ubuntu 7.10 machine) and simply installed (for all users) the appropriate fonts.

it is not elegant but it worked for me.

ShaulA

---

### Post by calande on 2007-11-03
Please use the xml files from here: [http://www.sharpfonts.com](http://www.sharpfonts.com)
Italic fonts will be aliased as on Windows.

---

### Post by tokinux on 2007-11-03
> **calande said:**
> Please use the xml files from here: [http://www.sharpfonts.com](http://www.sharpfonts.com)
Italic fonts will be aliased as on Windows.

Thanks much! These new xml files worked perfectly. Everything nice and crisp now \\:D/

---

### Post by cookies on 2007-11-03
Me again. I feel like a Troll. D:

Verdana, Tahoma, and Trebuchet MS do not display properly in bold. They are blocky.

Also, could you pretty please apply these rules to non-latin, if you can? That'd be awesome.

---

### Post by Elman on 2007-11-07
Is there any way I can change Firefox's fonts without changing all the System's?

Websites look terrible in smooth fonts cause they're usually supposed to be seen in sharp fonts, but the rest of the OS looks awesome. I don't want Firefox to look so terrible, but I want to keep the rest of the fonts :(

Thanks.

---

### Post by calande on 2007-11-07
I only know how to do the other way around: sharp fonts in the system and polished fonts in Firefox.

---

### Post by Elman on 2007-11-07
I've found a "mozilla-fonts" package for NetBSD that seems to do what I want. Would that work in ubuntu? :S

EDIT: Nevermind. I fixed it by disabling the "Allow pages to choose their fonts" option and using Sans-Serif 16 as default.

---

### Post by kingofpain on 2007-11-12
Hey!

Sorry I don't have the time to read all posts here (over 30 pages... oohh)
So, maybe my question was already asked.
The tahoma **bold** font (I got it from my windows installation) looks very bad. Could something be done?
And if so, could you post this on the first page, pls...

---

### Post by pcolamar on 2007-11-13
Walkerk, Calande,
  thanks a lot.
Everything has worked fine on my Gutsy installation.
That's an other step into my "escape from Windows"  venture.

Cheers

Palmer

---

### Post by calande on 2007-11-13
> **kingofpain said:**
> The tahoma **bold** font (I got it from my windows installation) looks very bad. Could something be done?
And if so, could you post this on the first page, pls...

Could you show us a screenshot please?

---

### Post by kingofpain on 2007-11-13
> **calande said:**
> Could you show us a screenshot please?

[[img]http://www.imagehost.ro/thumbnail.php/14020314473a3b4215633.png[/img]](http://www.imagehost.ro/viewer.php?img=14020314473a3b4215633)

[[img]http://www.imagehost.ro/thumbnail.php/14020425473a3b89f223c.png[/img]](http://www.imagehost.ro/viewer.php?img=14020425473a3b89f223c)

---

### Post by calande on 2007-11-13
Oh, wow, first time I see that... Are you using a standard installation? Are you using 96dpi? What desktop environment are you using?

---

### Post by kingofpain on 2007-11-14
> **calande said:**
> Oh, wow, first time I see that... Are you using a standard installation? Are you using 96dpi? What desktop environment are you using?

Yes... I use Gusty now... this thing I've noticed also on Feisty.
And yes, 96dpi.
I am using Gnome (Ubuntu Gutsy).

You should try to replicate this. Just find tahoma.ttf and put it in your fonts folder.

---

### Post by walkerk on 2007-11-14
Here is a script for sharpfonts.com...

```
cd /path/to/file
```
```
chmod +x sharpfonts.sh
```
```
./sharpfonts.sh
```

Enjoy.

---

### Post by gladstone on 2007-11-14
> **kingofpain said:**
> Hey!

Sorry I don't have the time to read all posts here (over 30 pages... oohh)
So, maybe my question was already asked.
The tahoma **bold** font (I got it from my windows installation) looks very bad. Could something be done?
And if so, could you post this on the first page, pls...

I've had this before. Make sure you have tahomabd.ttf installed aswell as the normal tahoma font. For some reason Ubuntu wouldn't work with the font I copied from my Windows install, but you can get a working one from here: [http://www.stchman.com/tools/MS_fonts/tahoma.zip](http://www.stchman.com/tools/MS_fonts/tahoma.zip) ([http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)) - notice there's two font files

---

### Post by maddog_326 on 2007-11-14
Thank you after all those years using windows the big font default on ubuntu was not a upside for me. Thank you for sharing this.:)

---

### Post by iml on 2007-11-15
For me the New York Times is the standard reference for serif, so I've got it to the point where it looks as good or better than Windows. 

[[IMG]http://img529.imageshack.us/img529/5614/s342tb0.th.png[/IMG]](http://img529.imageshack.us/my.php?image=s342tb0.png)

Subpixel smoothing and slight hinting. I also use [NoSquint](http://urandom.ca/nosquint/) for Firefox with a default zoom of 110%.

---

### Post by kingofpain on 2007-11-15
> **gladstone said:**
> I've had this before. Make sure you have tahomabd.ttf installed aswell as the normal tahoma font. For some reason Ubuntu wouldn't work with the font I copied from my Windows install, but you can get a working one from here: [http://www.stchman.com/tools/MS_fonts/tahoma.zip](http://www.stchman.com/tools/MS_fonts/tahoma.zip) ([http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)) - notice there's two font files

Thanks a lot! It works! =D>

---

### Post by imbjr on 2007-11-15
Thank you so much. After realising that my Tahoma fonts were incomplete and in the wrong location, I then applied your XMLs and my eyes are now crying with relief - though, oddly, they are now going to have to get back into the habit of looking at nice, crisp fonts.

Interestingly, the sharpfonts.com site process seemed overkill for me. All I needed was your original advice, no need to install anything else than the fonts and the XML.

---

### Post by cookies on 2007-11-17
I was looking at the configuration files, and this _[Guide Here](http://www.convexhull.com/mandrake_fonts.html)_, and I realized that we can disable Anti-Aliasing for font sizes below and equal to 13 that are not bold, and substitute some fonts for Bitstream Vera and the like, so you can have Sharp Fonts anywhere.

The config files are attached if you're interested.

---

### Post by gladstone on 2007-11-24
cookies: I've applied your edited xml files, I was wondering what the difference is with these and the ones on sharpfonts.com??

---

### Post by calande on 2007-11-24
I'm not sure but I think the old XML files have Arial and Dejavu Sans as default font families for sans-serif while SharpFonts have Tahoma and Dejavu Sans Condensed for sans-serif.

---

### Post by calande on 2007-11-24
> **imbjr said:**
> Interestingly, the sharpfonts.com site process seemed overkill for me. All I needed was your original advice, no need to install anything else than the fonts and the XML.

It's actually the exact same process, it just has more information and comments :)

---

### Post by corefile on 2007-11-26
> **Elman said:**
> I've found a "mozilla-fonts" package for NetBSD that seems to do what I want. Would that work in ubuntu? :S

EDIT: Nevermind. I fixed it by disabling the "Allow pages to choose their fonts" option and using Sans-Serif 16 as default.

wow, that is just what I needed, I'm fine with how my fonts looked, its was just the firefox ones, this fixed them up just right

---

### Post by gladstone on 2007-11-27
Is it possible to make only certain fonts "anti-aliased" - say Bitstream Vera Sans Mono, within using the "sharpfonts" xml files?

---

### Post by calande on 2007-11-27
Yes, the sharpfonts XML files do just that, with them you have antialiasing for all non-Microsoft fonts :)

---

### Post by lmo on 2007-11-30
I struggled, but eventually got the sharp fonts to work!:popcorn:

Personally, I much prefer putting my special fonts  in my home directory under .fonts and as well as using .fonts.conf as the xml for special fonts instead of system wide.

---

### Post by cookies on 2007-12-01
> **gladstone said:**
> cookies: I've applied your edited xml files, I was wondering what the difference is with these and the ones on sharpfonts.com??

Mine disable anti-aliasing for ALL fonts, calande's are for certain fonts.

---

### Post by apothecaryaaron on 2007-12-01
Worked for me.  Thanks!

---

### Post by lmo on 2007-12-01
I was amazed that without the xml files, these fonts look remarkably similar to cleartype fonts. Adjustments to the rgba sub-pixel hinting of none, rgb, bgr, vrgb, and vbgr will then affect the colored-haze. With the xml files, you can't get the colored haze.

Then I went over to XP and fiddled with
[[color=blue]ClearType Tuner PowerToy[/color]](http://www.microsoft.com/typography/ClearTypePowerToy.mspx) :-({|=

---

### Post by Bandicoot on 2007-12-01
I must say that I am very satisfied with the way my fonts look after I applied the xml file. My fonts look very crisp and webpages are rendered just the way I like them (I mean the displaying of text ofcourse). The only thing I dislike so far are when font are Italic, some font look really weird then. I have enclosed an example of tahoma 8 pt italic, they look very weird to me. I've also enclosed a picture to show just how sharp my webpages look now (big thumbs up !)

---

### Post by calande on 2007-12-01
Yeah, sadly the italic version is not as good as in Windows. I suspect this is due to Freetype's rendering algorythm, but I'm not 100% sure. If some one finds a way to enhance italic font rendering, I'd be happy to add it.
Thanks.

---

### Post by lmo on 2007-12-01
Tahoma maybe, does not have built-in italic ...

One of my "font.conf" files has this:
```
<!-- 
 Artificial oblique for fonts without an italic or oblique version
 -->
 
	<match target="font">
		<!-- check to see if the font is roman -->
		<test name="slant">
			<const>roman</const>
		</test>
		<!-- check to see if the pattern requested non-roman -->
		<test target="pattern" name="slant" compare="not_eq">
			<const>roman</const>
		</test>
		<!-- multiply the matrix to slant the font -->
		<edit name="matrix" mode="assign">
			<times>
				<name>matrix</name>
				<matrix><double>1</double><double>0.2</double>
					<double>0</double><double>1</double>
				</matrix>
			</times>
		</edit>
		<!-- pretend the font is oblique now -->
		<edit name="slant" mode="assign">
			<const>oblique</const>
		</edit>
	</match>

```Changing the "0.2" to "0.3" resulted in a better-looking italic for Tahoma. I haven't checked to see what it did to any other fonts, though.

---

### Post by cookies on 2007-12-01
> **lmo said:**
> Tahoma maybe, does not have built-in italic ...

One of my "font.conf" files has this:
Changing the "0.2" to "0.3" resulted in a better-looking italic for Tahoma. I haven't checked to see what it did to any other fonts, though.

Looks like it won't do much, it only does it for fonts with no italic form. (I wonder if this is possible for bold, too?)

---

### Post by calande on 2007-12-01
I know this snippet, it's intended to fonts that weren't designed with italic support in mind, it simulates italic, but Tahoma does have an italic variant. I'm on Windows XP at the moment and Tahoma Italic doesn't look very nice here either! :)
I think italic fonts don't look very well, be they aliased or not, actually :(

---

### Post by lmo on 2007-12-01
I must have missed a trick somewhere, because my Tahoma doesn't do its own italic and obeys the snippet. I must have been lucky -- I think it looks better. Looks like this:

---

### Post by lmo on 2007-12-02
> **kingofpain said:**
> Hey!

Sorry I don't have the time to read all posts here (over 30 pages... oohh)
So, maybe my question was already asked.
The tahoma **bold** font (I got it from my windows installation) looks very bad. Could something be done?
And if so, could you post this on the first page, pls...Some sources of these fonts have the bold that looks bad. At first, I got the ones that looked bad. To fix, I got the fonts from a different source.

I suppose that the fonts offered in this thread look good.

---

### Post by gladstone on 2007-12-02
> **cookies said:**
> Mine disable anti-aliasing for ALL fonts, calande's are for certain fonts.

And enable anti-aliasing on bold fonts right? I prefer yours with bold fonts, for example on Wikipedia headings

I want the anti-aliasing of bold fonts but the aliasing of only Microsoft fonts as per calande's XML files (so I can use Bitstream Vera Sans again)

Can someone help me with that?

---

### Post by lmo on 2007-12-02
> **calande said:**
> I know this snippet, it's intended to fonts that weren't designed with italic support in mind, it simulates italic, but Tahoma does have an italic variant. I'm on Windows XP at the moment and Tahoma Italic doesn't look very nice here either! :)
I think italic fonts don't look very well, be they aliased or not, actually :(Since I am a font trainee, I don't know why one system thinks Tahoma has italic and another system thinks it doesn't. However, with my trusty sledgehammer, I was able to affect the slant of the Tahoma italic anyway by adding this section:```
        <match target="font">
                <!-- check to see if the font is ?HUH? -->
                <test name="family">
                        <string>Tahoma</string>
                </test>
                <!-- check to see if the pattern requested non-roman -->
                <test target="pattern" name="slant" compare="not_eq">
                        <const>roman</const>
                </test>
                <!-- multiply the matrix to slant the font -->
                <edit name="matrix" mode="assign">
                        <times>
                                <name>matrix</name>
                                <matrix><double>1</double><double>0.2</double>
                                        <double>0</double><double>1</double>
                                </matrix>
                        </times>
                </edit>
                <!-- pretend the font is oblique now -->
                <edit name="slant" mode="assign">
                        <const>oblique</const>
                </edit>
                <!-- and disable embedded bitmaps for artificial oblique -->
                <edit name="embeddedbitmap" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>
```Modifying the "0.2" higher/lower made more/less slant. I don't know if the "bitmap" is needed or what it does. "-0.2" goes backwards. :)

---

### Post by Bandicoot on 2007-12-02
hmm very strange. I was playing around a little with Firefox 3, and noticed that it doesn't render italic for this forum while Firefox 2 does. I've included two screenshots from the exact same page, the first in Firefox2 and the second in firefox 3.

---

### Post by cookies on 2007-12-02
> **gladstone said:**
> And enable anti-aliasing on bold fonts right? I prefer yours with bold fonts, for example on Wikipedia headings

I want the anti-aliasing of bold fonts but the aliasing of only Microsoft fonts as per calande's XML files (so I can use Bitstream Vera Sans again)

Can someone help me with that?

That's doable. I'll fiddle around and see what happens. :p

Edit:
[Try these files and tell me how they work.]("http://files.filefront.com/font+config+filestargz/;9176747;/fileinfo.html")

---

### Post by gladstone on 2007-12-06
Cookies: Thanks, this is just what I wanted and it looks the best combination to my eyes!

One last thing I want to change is to put some AA on these:

[[IMG]http://thumbnails.freeimagehost.eu/163/a7f4351628239.gif[/IMG]](http://www.freeimagehost.eu/image/a7f4351628239)

e.g. Level 1 headings on Wikipedia

---

### Post by JohnOhl on 2007-12-06
> **gladstone said:**
> Is it only me, or does Cleartype/Font Anti-aliasing/Smoothing whatever you want to call it look as bad as I think it does?

I really can't see the appeal of blurry fonts. Everyone say's it's designed for LCD's in mind, but I just can't get on with them on my laptop - perhaps it's my screen?

Anyway, running through this process (it's a shame I didn't find this thread to start with) was the first thing I did when installing Ubuntu - perhaps I'm being too hasty?

It could be your screen resolution, I only like it setup like this when the screen resolution is higher than 1280x1024 and the font sizes are set below 10, personally I prefer 8 :P.

Anything below 1280x1024 and any fonts > 10 look better in linux fonts imho

---

### Post by cookies on 2007-12-07
> **gladstone said:**
> Cookies: Thanks, this is just what I wanted and it looks the best combination to my eyes!

One last thing I want to change is to put some AA on these:

[[IMG]http://thumbnails.freeimagehost.eu/163/a7f4351628239.gif[/IMG]](http://www.freeimagehost.eu/image/a7f4351628239)

e.g. Level 1 headings on Wikipedia

Try the attached file. Read the README, too, please.

---

### Post by Bandicoot on 2007-12-09
Is there a way to make my fonts in open office look smooth ? I know OO has its own rendering engine, I've set aliasing for fonts on 12 but the fonts still look horrible...I've enclosed a screenshot to show what I mean. Is this the best result I can get ?

---

### Post by cookies on 2007-12-09
> **Bandicoot said:**
> Is there a way to make my fonts in open office look smooth ? I know OO has its own rendering engine, I've set aliasing for fonts on 12 but the fonts still look horrible...I've enclosed a screenshot to show what I mean. Is this the best result I can get ?

Try 17, OO.O is specifying pixel sizes, not point sizes.

---

### Post by calande on 2007-12-10
OO.o is weird. Try restarting it, it may change its rendering for Times New Roman. Here I restarted and it now displays fonts like WinXP.

---

### Post by Bandicoot on 2007-12-10
:mad: Still not good. The fonts keep looking smudgy no matter what I do..

---

### Post by lmo on 2007-12-11
I can't make Ooo look good either :mad:

---

### Post by calande on 2007-12-11
Just in case, OpenOffice.org uses its own font-rendering engine, so you have to go through the menu "Tools > Options > OpenOffice.org > View" and set "Screen font antialiasing" to "12px" or smaller.

---

### Post by Bandicoot on 2007-12-11
:( that's exactly what I allready did : in my first post about this I say:

Is there a way to make my fonts in open office look smooth ? I know OO has its own rendering engine, I've set aliasing for fonts on 12 but the fonts still look horrible...I've enclosed a screenshot to show what I mean. Is this the best result I can get ?

---

### Post by lmo on 2007-12-11
Oooooh ... I can get subpixel rendering everywhere except Ooo.  :-s
[Too unbelievable, but true...](http://ubuntuforums.org/showthread.php?t=406273)

---

### Post by Orbital75 on 2007-12-12
Looks good..... thanks  :)

---

### Post by timzak on 2007-12-16
To the thread starter...thank you!  My eyes say "Ahhhhh!".  I can't tell you how long I've been trying to get used to and "like" the font smoothing in Ubuntu.  I thought it was me just being thick-headed, but moment I applied your fix, my eyes relaxed.

Maybe it's my monitor as I still use a CRT (19" @ 1280 x 960), but I've been using Ubuntu for 8 months now and just couldn't get used to the font smoothing.

A big thanks again.

---

### Post by Bandicoot on 2007-12-18
I made a small adjustment to your configuration file ( I made arial bold smaller than 12 aliased instead of antialiased) makes them look less smooth but alot sharper ..When using google arial bold looked a bit smudged and they look sharp now , but I gues that's a matter of personal preferences.

I was wondering if it is possible to turn italic off for some fonts ? I can't seem to find the setting to do that. As I mentioned before arial italic look awful so I was looking for a way to turn italic of for this font.

NB: I have enclosed a file which shows how google/Arial bold looks aliased instead of antialiased

---

### Post by Naatan on 2008-01-15
Anyone know how to uninstall this?

---

### Post by calande on 2008-01-15
Easy :)
Remove the files you installed.

---

### Post by Naatan on 2008-01-15
I don't think that would work as when you install it - it overwrites the default files, so when I would simply delete the installation files, wouldn't I be missing the files that I need ?

---

### Post by calande on 2008-01-15
What original files did it overwrite?

---

### Post by Naatan on 2008-01-15
I can't say if it did indeed overwrite anything but im guessing it should have, otherwise how would the system pick up on the changes..

the files it extracted in /etc/fonts/ are;

alias.conf
local.conf
misc.conf
msfonts-rules.conf

---

### Post by unshareef on 2008-01-19
Dear Charles, I would like to revert, but when I try to erase the local file it says I don;t have the permission to do so. Any way out?

Thanks

---

### Post by calande on 2008-01-19
> **Naatan said:**
> I can't say if it did indeed overwrite anything but im guessing it should have, otherwise how would the system pick up on the changes?

Fontconfig works this way: fonts.conf checks if a local.conf file exists. If there is a local.conf file in the same directory, fonts.conf imports it. Otherwise, it doesn't generate any error.

> **unshareef said:**
> Dear Charles, I would like to revert, but when I try to erase the local file it says I don;t have the permission to do so. Any way out?

Yes, you need to be root to remove system files. Here's what you need to do in your terminal:

```
sudo rm -f /etc/fonts/local.conf
```

Be careful not to running something else, because you have root privs.

---

### Post by andrebrait on 2008-01-23
wow! Worked like a charm! Very good! Some fonts, when anti-aliased, were annoying and very strange/unreadable, now they're good!

There should be a button somewhere to turn anti-aliasing on and off when you want

---

### Post by calande on 2008-01-23
> **andrebrait said:**
> wow! Worked like a charm! Very good! Some fonts, when anti-aliased, were annoying and very strange/unreadable, now they're good!

Cool! :)

> **andrebrait said:**
> There should be a button somewhere to turn anti-aliasing on and off when you want

There ya go :)

[IMG]http://i31.tinypic.com/149d15y.png[/IMG]

---

### Post by wyslij on 2008-01-29
I've read the entire thread and still don't understand this - maybe I'm just not meant to work in Linux...

I've installed Gutsy and MS fonts and Tahoma from my Windows installation and the fonts work just fine... but without anti-aliasing (cleartype).

The rest of Linux fonts have cleartype and the MS fonts not really.

And I want all of my fonts and especially Verdana, Tahoma and Times New Roman to have anti-aliasing (cleartype) in web pages - I'm just used to that and I like it a lot.

Please can someone explain to me in simple steps how to enable anti-aliasing (cleartype) for all my Windows Fonts in my Gutsy (7.10) installation?

Please help...

---

### Post by calande on 2008-01-29
> **wyslij said:**
> but without anti-aliasing (cleartype)

Cleartype means antialiased (polished) to make it simple.

> **wyslij said:**
> Please can someone explain to me in simple steps how to enable anti-aliasing (cleartype) for all my Windows Fonts in my Gutsy (7.10) installation?

A default Linux distro such as Ubuntu already has antialiasing enabled by default. Nothing else to do, and especially, do *not* install the XML files from this tutorial.

---

### Post by wyslij on 2008-01-29
> **calande said:**
> Cleartype means antialiased (polished) to make it simple.

A default Linux distro such as Ubuntu already has antialiasing enabled by default. Nothing else to do, and especially, do *not* install the XML files from this tutorial.

I know - and MOST of my fonts are antialiased, but when I installed Verdana, Tahoma and other Windows fonts - they are not antialiased and I want them to be...

Are your Windows fonts antialiased? Did you do anything to make it happen?

I like how Ubuntu does anti-aliasing, but I don't understand why it doesn't to it to the Windows fonts...

Please help - I need to have my Windows fonts in Linux antialiased as well

---

### Post by calande on 2008-01-29
> **wyslij said:**
> I know - and MOST of my fonts are antialiased, but when I installed Verdana, Tahoma and other Windows fonts - they are not antialiased and I want them to be...

As I said, if you want fonts to be antialiased, don't install the XML files of this tutorial.

> **wyslij said:**
> Are your Windows fonts antialiased?

No they aren't. I use these XML files. What this configuration does is mimic the Windows XP way of rendering fonts, that is: Antialias any font at any size, except the Microsoft fonts under a specific size, and according to a few more criteria.

> **wyslij said:**
> I like how Ubuntu does anti-aliasing, but I don't understand why it doesn't to it to the Windows fonts...

It doesn't do it to the Windows fonts because you installed the XML files.

> **wyslij said:**
> Please help - I need to have my Windows fonts in Linux antialiased as well

Just remove the XML files you extracted, and hit Ctrl-Alt-Backspace to restart X.

---

### Post by wyslij on 2008-02-01
Thanks - you're so right... the XML file messed it up - I mean - disabled antialiasing - I removed the files and it works perfectly now - just the way I want it.

Enjoying Ubuntu and Windows fonts on Ubuntu :-)

---

### Post by calande on 2008-02-01
Arfh...At least show us a screenshot to celebrate! :)

---

### Post by brijeshchauhan on 2008-02-05
It works fine but has a small problem:confused:. All the fonts in firefox ()seems like they are  squeezed horizontally. They are not as comfortable as in windows. Does anybody have the solution?

---

### Post by brijeshchauhan on 2008-02-05
I think this just removes antialising, its not changing any fonts for me. I can see that it has installed all the MS fonts, but it doesnt change any font.

Do I have to manually change the fonts for applications and all or the XML file should have changed the fonts for me?

---

### Post by brijeshchauhan on 2008-02-05
> **calande said:**
> No, not a genius, but it took a fair amount of time due to sparse documentation.
Namaste,

Hey, you know Hindi or what?

---

### Post by brijeshchauhan on 2008-02-05
> **calande said:**
>  Nothing else to do, and especially, do *not* install the XML files from this tutorial.

Actually I have installed the XML file. How do I remove it? Should I just remove local.conf file?

---

### Post by googlah on 2008-04-02
Thanks :)  Much easier to read now.

---

### Post by deepclutch on 2008-04-30
thanks!but with nvidia proprietary drivers,you dont need these settings?for me it works perfectly.

---

### Post by MemoryDump on 2008-04-30
does this how-to still work under hardy? is it even needed?

---

### Post by kevin66 on 2008-04-30
Thanks alot.

---

### Post by gladstone on 2008-05-05
Just quickly, I was wondering if there is anything similar to Window's "standard" font smoothing? - When I say standard, it is an option from the following:

1. None - (what these configs achieve)
2. Standard
3. Cleartype

in display\appearance\effects (or something like that ;))

---

### Post by cookies on 2008-05-05
> **gladstone said:**
> Just quickly, I was wondering if there is anything similar to Window's "standard" font smoothing? - When I say standard, it is an option from the following:

1. None - (what these configs achieve)
2. Standard
3. Cleartype

in display\appearance\effects (or something like that ;))

These technically are the "Standard" type in Windows.

---

### Post by Woormy on 2008-05-10
> **MemoryDump said:**
> does this how-to still work under hardy? is it even needed?

I just set it up in Hardy and it works great.

---

### Post by amisdar on 2008-05-18
Thanks calande! When I first using Ubuntu a month ago, I wonder what is missing. The desktop, icon, etc looks great but somehow I just don't don't get the feeling when I'm working on it.

After a while then only I realized that my eyes don't feel comfortable with the font.

And here I am using your mods to fix it.

I really enjoy Ubuntu now!

Thanks again for this useful guide! :KS

---

### Post by hanzahar on 2008-05-19
tar: alias.conf: Cannot open: Permission denied
tar: local.conf: Cannot open: Permission denied
tar: misc.conf: Cannot open: Permission denied
tar: msfonts-rules.conf: Cannot open: Permission denied
tar: Error exit delayed from previous errors

:(

---

### Post by imbjr on 2008-05-19
> **MemoryDump said:**
> does this how-to still work under hardy? is it even needed?

I thought I'd try to tolerate the font-look when I installed Hardy but I soon cracked and went to sharpfonts.com to get ma fix.

---

### Post by Ry12 on 2008-06-06
Is it possible to render these fonts like they are rendered under windows when using cleartype?

---

### Post by audioduck on 2008-06-07
[FONT="Verdana"]Nice tip mate. That worked perfectly.

Cheers![/FONT]

---

### Post by djarcadian on 2008-06-08
Thanks for this calande! Ubuntu looks much nicer now. 

My only suggestion is to include instructions for changing directories. I download my files to the Desktop and had some trouble figuring out how to extract some of the files.

---

### Post by dryder on 2008-06-08
> My only suggestion is to include instructions for changing directories.

Did you try googling "ubuntu change directories"? A lot of self-help info is out there. :)
David

---

### Post by sempronius on 2008-06-30
> **gladstone said:**
> Just quickly, I was wondering if there is anything similar to Window's "standard" font smoothing? - When I say standard, it is an option from the following:

1. None - (what these configs achieve)
2. Standard
3. Cleartype

in display\appearance\effects (or something like that ;))


This is exactly what I would also like to achieve!

With anti-aliasing enabled, fonts in Linux look somewhat blurred and are hard on my eyes though they look nicer. With anti-aliasing disabled, my eyes feel all right (which, of course, is more important than anything else), but the look of the fonts is less than satisfying, fonts look "scratchy", dirty, not smooth at all.

When I compare this to Windows XP, I must say that I am disappointed!
Fonts in XP look GREAT, with anti-aliasing set to "standard font smoothing" (or whatever it is called in English versions of XP) (maybe "default font smoothing", maybe "standard font smoothing", I can't know for sure...).

I use a CRT monitor, so cleartype is not what I want. So instead of chosing cleartype in XP or disabling anti-aliasing I just select "standard font smoothing", and this gives me absolutely perfect font quality: easy on my eyes, but still smooth, not really blurry at all!

I would like to achieve the exact same appearance as this "standard font smoothing" in Linux, too. But how - if even possible?


Regards, sempronius

EDIT:
Here are some links to screenshots I made; I would like to hear which one you like most (which one looks the best, which one is easy or hard on your eyes etc.):

1.
[http://www.ld-host.de/show/be6716929791fd987b0a7eccca67a8be.png](http://www.ld-host.de/show/be6716929791fd987b0a7eccca67a8be.png)


2.
[http://www.ld-host.de/show/7a989da887607eb00a17acccccb3568d.png](http://www.ld-host.de/show/7a989da887607eb00a17acccccb3568d.png)


3.
[http://www.ld-host.de/show/86c9af5e8c9a4d060edb0ff1e42c2731.png](http://www.ld-host.de/show/86c9af5e8c9a4d060edb0ff1e42c2731.png)

---

### Post by hgurol on 2008-07-02
Its #3 for me both for the "best looking" and "easy on eyes"...

#1 comes as second and #2 is nowhere near usable for me.

Which one is which setting?

Im also wondering if the experience will be the same as looking at your screenshots if I go ahead and start to use the same settings.

---

### Post by sempronius on 2008-07-02
> **hgurol said:**
> Its #3 for me both for the "best looking" and "easy on eyes"...

#1 comes as second and #2 is nowhere near usable for me.

Which one is which setting?

Im also wondering if the experience will be the same as looking at your screenshots if I go ahead and start to use the same settings.


Congratulations, hehe :-)

Your choice (#3) is also mine. And, doh, it is windows xp with standard font smoothing (not cleartype). This is what I try to achieve in Linux, too.

#1 is my worst choice, however. It is Linux with anti-aliasing turned on. It is too blurry and the characters are a bit too thick as compared to xp.

#2, in fact, has been what I have been using in a long time under Linux!
It is without anti-aliasing. While the characters don't have a nice look, readability is not that bad - this lack of font smoothing is good for my eyes.


In the mean-time, I made some progress...

By comparing my regular Linux system to a so called live cd (called "slax" - it is slackware based) I found that fonts in Linux do NOT necessarily look that bad: Under Slax the font quality is almost the same as under XP for me.

So I wondered why, and I think, I already got some clues:

I found that under Slax the bytecode interpreter of libfreetype is NOT enabled - so paradoxically, I don't get bad font results, but, interestingly, better results when the byte interpreter is disabled.

What I also found is that on my regular system fontconfig-config was set to "native". I made a test and set it to "autohinter" and got better results than with "native"!!

dpkg-reconfigure fontconfig-config....

Currently, I am recompiling and testing the most recent version of libfreetype and trying out:
a) with bytecode enabled / native
b) with bytecode enabled / autohinter
c) without bytecode / native
d) without bytecode / autohinter

Would like to hear your experiences, thanks for your reply, hgurol.


Regards, sempronius

---

### Post by hgurol on 2008-07-03
I dont have much experience to share sempronius, sorry.

A couple of months ago I wanted to completely switch to ubuntu. Installed 7.10 and spent sometime with it. During that time this fonts/anti-aliasing was a serious issue for me. I have tried whatever trick, config I have found on this forum but I have never managed to get the same look&feel of your #3 screenshot. However, I have managed to get to a point where I can still be happy with it.

The problem is; since I have tried so many different things at one time, reverted back some changes and kept some of them etc. I could never know which setting or config provided the closest XP look for me.

At that time I couldnt manage to perminantly move onto ubuntu due to some other issues(converting my pst files was a serious head ache for example). Now Im gonna try again. I might have less issues with 8.04   I wish I knew what config I did to improve my font rendering in the past. I need to figure it out once again.

Im sure this is not the experience you would expect to hear but unfortuantly this is the only one I have :)

Please keep us posted with your progress and findings...

---

### Post by -Outcast- on 2008-07-04
I am with sempronius on this one.

In ooowriter I was having font probs even with the MScore downloaded. 

I did as this post instructed. but the system fonts changed and I did not like 

With anti-aliasing on I know it's badddd. Then off I can at least write for hours without wondering if my eyesight is going bad. 

But it still looks poor. 

Tried Arial and it's better. Not my favourite to read but still better than times at the moment. 

I removed the Local file, but there's still other stuff behind. Is it ok to remove that to? 

Any one seen what Mint looks like?

---

### Post by -Outcast- on 2008-07-04
sorry forgot to subscribe

---

### Post by kregg on 2008-07-07
If everyone is experiencing Ubuntu having weird (but true to Microsoft) fonts on their system, they may like to change it to something different.

If you go to System>Preferences>Appearances and go to the Fonts tab and have the following setup:
[[IMG]http://img84.imageshack.us/img84/3171/screenshotappearancepreom8.png[/IMG]](http://imageshack.us)
[[IMG]http://img84.imageshack.us/img84/3171/screenshotappearancepreom8.6c1a8e573a.jpg[/IMG]](http://g.imageshack.us/g.php?h=84&i=screenshotappearancepreom8.png)

It should make your Ubuntu look nice again. :D (Font smooting is optional for you).

---

### Post by hgurol on 2008-07-07
Its not about choosing a better font, its about rendering the font...

---

### Post by sempronius on 2008-07-15
> **hgurol said:**
> Its not about choosing a better font, its about rendering the font...

Exactly!

One can look for fonts all the time, but the basic problem will not be solved: having good font rendering.

There may, indeed, be some subtle differences between different versions of libfreetype that make fonts more or less blurry, but I cannot, as much as I try, achieve the same degree of good looking and easily readable fonts as under Windows XP - with "standard font smoothing". Cleartype is horrible, for me, on a CRT, but standard font smoothing is phantastic, beautiful!

1) Does someone know if there have been changes between windows 2000 (or windows 98/me) and windows xp regarding font smoothing?
I know that windows 2000 lacks cleartype, but it DOES offer normal, standard font smoothing. The quality, with otherwise identical settings, however, is worse than under XP - in fact, it is very much like the Linux quality I get. ;-)

2) Another question:
How many libraries can contribute to the the quality of font rendering and the degree of smoothing fonts? Does anybody know?
Well, obviously, libfreetype is important! And the way it has been compiled.
But what about libXft, libfontconfig, libXrender, libXfont......etc. etc.?

Does anybody know if playing with libfreetype alone is not sufficient, but that different versions of the above (or one of them) other libraries also change font rendering itself?


Another observation I made:
It is not just anti-aliasing (font smoothing) that makes Linux fonts blurry (for me) - the fonts even without any anti-aliasing are already less clear, less sharp than under windows xp. So it doesn't appear as a mere problem of anti-aliasing, it is a fundamental problem of Linux (or xorg) font rendering, methinks.

Ideas?

Oh, and something more:
For a long time I wouldn't realize, but working for hours under Linux reading texts in a browser caused severe eye strain and - quite often - headache, too.
I used to find this normal considering the fact that I was reading for hours.

But wait...
During the last few months I used XP quite often - and much to my surprise: I can read for hours and hours, and my eyes do NOT feel strained, my head does NOT start to ache. 
Sad, isn't it?


Regards, sempronius

---

### Post by -Outcast- on 2008-07-16
sempronius: You wrote that well! 

This thing really needs to be addressed. I can watch a movie on linux but not write a book! 

I am forced back to Vista to write due to this issue on linux. Then again on vista openoffice writer lacks a keyboard buffer and hangs when autosaving so I am now thinking of having to quit opensource and go for Word. Depressing. But at least it works. 

I never remember having these problems 5 years ago? Maybe it's just me. 

Anyway. Do all Linux distros have this problem with rendering? OR is there one out there that displays a font well enough to write for 8 hours straight?

---

### Post by pitup on 2008-07-28
The joke is that MS started to use blurry antialiased fonts in Office 2007. Also Adobe Reader 9 for XP adopted such a way of displaying fonts.
But in MS Office 2007 and Adobe Reader 9 you can easily turn off antialiasing competely and everything looks great again.
As to Linux - I spend days in searching for a solution and found nothing satisfying... Some hacks allow to come rather close to XP, but still it's not match...

I can't thoroughly migrate to Linux because I really hate the look of antialiased fonts :(

Maybe we should add this issue into some Ubunu bug-tracker or wishlist?

---

### Post by sempronius on 2008-07-28
> **pitup said:**
> The joke is that MS started to use blurry antialiased fonts in Office 2007. Also Adobe Reader 9 for XP adopted such a way of displaying fonts.
But in MS Office 2007 and Adobe Reader 9 you can easily turn off antialiasing competely and everything looks great again.
As to Linux - I spend days in searching for a solution and found nothing 



For me, it is not a question of anti-aliasing or not, but about the font rendering itself in Linux.

Actually, I like the way windows XP does anti-aliasing.
CAREFUL:
I do NOT speak of so called "cleartype", but of the standard method to do font smoothing, this method has already been available in windows 2000 and in windows millennium (and others, I guess). XP only added cleartype.

Using the standard method of font smoothing (not cleartype!), I get fonts that look great - okay, they are smoothed, but nevertheless, I do not find them blurry at all. I can compare between a CRT and a TFT monitor, but in either case I avoid cleartype and chose standard font smoothing. It is not as rough as no anti-aliasing at all and it is still not really blurry.

Linux, however, with or without subpixel hinting, does not reach the same degree of good looking, non-blurred, but still somewhat smoothed fonts.

I would welcome any useful comment to my question if it is possible to manipulate the DEGREE of anti-aliasing in Linux (the degree of anti-aliasing, NOT the degree of hinting - that is something different!).

To be honest, with a TFT monitor instead of my CRT things have improved. Now anti-aliasing combined with RGB subpixel hinting provide for comparatively good looking fonts. Still miles away from the crisp and sharp (but not rough) font rendering in XP.

What I also find highly annoying is the fact that fonts in Linux often look very thin and are - for this reason - hard to read, while all of a sudden they jump to some rather thick appearance when increasing the size. Both the very thin and the rather thick appearance doesn't please my eyes.

But it also depends on the web site makers. Some sites actually look quite good under Linux, and with anti-aliasing turned off!

Look here, for instance:

h**p://de.opensuse.org/Projektübersicht

This MS Trebuchet font on this site looks good for me.


Anyway, fonts are a weak spot in Linux and if you ask me, something MUST be done to improve the situation.

Just out of curiosity, I burned a live cd of Freebsd, but since this OS also uses a normal Xserver, freetype etc. (if I am not wrong), fonts look as modest there as under Linux.


sempronius

---

### Post by 35712 on 2008-08-06
Hey guys!

I am pretty discouraged right at the moment. I cannot get my microphone working and my installed sharp fonts are ugly again. It began with Firefox and spread quickly after the attempt to reinstall the fonts again over the whole system. Now hinting still has an effect, but subpixel hinting and Anti Aliasing not at all.

All I did regarding fonts or anything was uninstalling Abiword mit all its parts. But that cannot have to do with it, can it?

Is this a known problem, that the sharp fonts just disappear?

Overall: They are still not as good as in Windows and I can hardly imagine working wuthout XP, cause it is really comfortable, though bloody slow.

---

### Post by davidryder on 2008-09-14
Wow that looks about 3x better. Thanks!

---

### Post by Dark Ocean on 2008-10-29
> **davidryder said:**
> Wow that looks about 3x better. Thanks!

Indeed! Works great!

---

### Post by prabath_fun on 2008-10-30
Hi,
  I copied the .ttf files from c:\windows\fonts and pasted in "microsoft"(folder created) at /usr/share/fonts/X11 in Ubuntu 8.04. I can able to use the Microsoft fonts in Open office, Thunderbird, etc., without any problem.
   Is it ok. Or I need to follow the installation of msttcorefonts.
Please update me.
[COLOR="Blue"]Prabath[/COLOR]

---

### Post by clubsoda on 2008-12-22
On Xubuntu Intrepid this suggestion is giving me some wacky rendering...

[img]http://ubuntuforums.org/attachment.php?attachmentid=97242[/img]

These should be Times New Roman and Trebuchet MS.
Any idea what´s going wrong here?


*Edit: Fixed spelling of "whacky". Must've seen too many mafia movies.*

---

### Post by calande on 2008-12-22
Wow...No idea, clubsoda, sorry :(
Any idea, anyone else?

---

### Post by clubsoda on 2008-12-24
I should have mentioned that I'm using a GeForce2 MX400 with the nvidia-glx-96 proprietary driver.  So I just deactivated the restricted driver and did a test with the Xorg **nv** driver, which works perfectly!  [Although glx-gears is back to 80 frames/second in this configuration.:)]

---

### Post by calande on 2008-12-24
Cool, nice to hear that, clubsoda, and thanks for sharing the info with us ;)

---

### Post by Arup on 2009-01-09
Thank you very much, fonts look very good in Opera and overall.

---

### Post by calande on 2009-01-09
You welcome! I'm happy you like the fonts, and Opera. Opera is my favorite application :)

---

### Post by runbei on 2009-01-15
Ruined my system fonts - menus in apps are now partially unreadable.

---

### Post by square_wave on 2009-02-12
For people who don't like antialiased fonts: try to change hinting from full to slight
In context of this guide it will be
```
<match target="font" >
        <edit mode="assign" name="antialias" >
                <bool>true</bool>
        </edit>
        <edit mode="assign" name="autohint" >
                <bool>true</bool>
        </edit>
        <edit mode="assign" name="hintstyle" >
                <const>**hintslight**</const>
        </edit>
</match>

```
in misc.conf
Will it help?

Also I tweaked msfonts-rules.conf to make antialiasing turn off at more adequate conditions (did not read the entire topic, maybe it was already done before)

---

### Post by haddog on 2009-02-17
Worked great in 8.04.2. Thnx!

---

### Post by Pawel Andrzej on 2009-02-18
Thank you, Charles. The instructions for downloading the fonts and then updating the XML repository worked perfectly. The fonts are nice and crisp now in 8.10. 

I can finally read on-line newspapers without eyestrain.

-Pawel

---

### Post by slickvguy on 2009-02-19
> **clubsoda said:**
> I should have mentioned that I'm using a GeForce2 MX400 with the nvidia-glx-96 proprietary driver.  So I just deactivated the restricted driver and did a test with the Xorg **nv** driver, which works perfectly!  [Although glx-gears is back to 80 frames/second in this configuration.:)]

After trying to get this working on my Ubuntu 8.10 w/ no success, I stumbled upon this post that showed the exact same problem I had. So I deactivated the nvidia accelerated graphics driver (GeForce4), rebooted (just to be sure), and voila - the "mess" went away. Success. Thank you, Club Soda et al.

Unfortunately, I'm not so sure I like the way this looks. Maybe I just have to get used to it. Certain elements look great, other stuff not so great. The basic look and feel is more modern/pleasant - but the text appears thin and "scratchy" looking. 17" LCD, subpixel, slight. I understand that the antialiasing is off and that this is going for a clearer look versus a muddier/rounded look. But is this the best it gets? If you look at the image I posted, see where it says "SPY Options" on the toolbar? Pretty ugly. Crooked letters. Any way to improve that?

Been working on fonts tonight. After I d/l'd the msttcorefonts, webpages displayed on FF3 looked SO much better (I have it set for the webpages to use "their own" fonts). I also did that linking to the 10-autohint.conf "trick" which seemed to make a difference too.

---

### Post by Pawel Andrzej on 2009-02-21
> If you look at the image I posted, see where it says "SPY Options" on the toolbar? Pretty ugly. Crooked letters.

It's still a great improvement over the original Intrepid fonts. I see where you're coming from though. It seems there should be a happy middle: crisp non-choppy fonts.

---

### Post by slickvguy on 2009-02-21
FWIW: I installed the Liberation fonts and find them to be a pleasant compromise.

---

### Post by calande on 2009-02-22
@slickvguy: I agree, they are nice (but only if antialiased and hinted).

---

### Post by googlah on 2009-02-24
Also look very good over here. Thanks for the tutorial, Ubuntu's default fonts.. you can't read it. Now it's acceptable. :biggrin:

---

### Post by Psyche on 2009-02-24
Hello, 
I installed Windows fonts but they still don't look like in Windows. For example, some of the fonts are very small. The font in this textarea is pretty small and I can hardly read it without eyestrain. Do I have to do some extra configuration? Thanks.

---

### Post by calande on 2009-02-25
Yes, in your application (e.g. Firefox), select a larger size for minimum font size.

---

### Post by toejamfootball on 2009-03-18
I recently re-installed xubuntu on my PC, this How to worked before I did this, but now it doesnt work I get this error when I type sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

tar: fontconfig.tbz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I read through this whole thread and it might have already been asked, but I couldn't find it.

Cheers.

---

### Post by toejamfootball on 2009-03-18
this is how it looked when I got it to work.

[[IMG]http://img8.imageshack.us/img8/3955/paypalk.th.png[/IMG]](http://img8.imageshack.us/my.php?image=paypalk.png)

This time it looks like this....

[[IMG]http://img24.imageshack.us/img24/4899/screenshotrcg.th.png[/IMG]](http://img24.imageshack.us/my.php?image=screenshotrcg.png)

---

### Post by calande on 2009-03-18
This is not the way it's supposed to look like (on either screenshot). Could you return the output of this please:

```
ls -l
```

When you try to run the tar command please? (I suspect the file you're trying to extract isn't in your current directory).

---

### Post by toejamfootball on 2009-03-18
You just want me to type that in terminal?

james@jimjam:~$ ls -l
total 28
drwx------ 2 james james 4096 2009-03-18 17:29 Desktop
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Documents
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Music
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Pictures
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Public
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Templates
drwxr-xr-x 2 james james 4096 2009-03-18 01:12 Videos
james@jimjam:~$

EDIT: If possible I would like to have it look like my first screenshot, I really liked that. Wish Id written down exactly how I got there... :D

EDIT: Sorry here it is -rw-r--r-- 1 james james 2013 2009-03-18 17:29 fontconfig.tbz

---

### Post by calande on 2009-03-18
This is what I thought...You didn't put the fontconfig.tbz file where you're running your terminal. Put the file in your home directory before running the command. But in any case, the fonts will look like the default Windows XP font rendering (different from your screenshots).

---

### Post by toejamfootball on 2009-03-18
> **calande said:**
> This is what I thought...You didn't put the fontconfig.tbz file where you're running your terminal. Put the file in your home directory before running the command. But in any case, the fonts will look like the default Windows XP font rendering (different from your screenshots).

Yeah thanks, I have had a friend helping me and we figured this much out.

Do you have any ideas how I could achieve the look of my first screenshot? I loved it that way.

---

### Post by calande on 2009-03-18
Actually, I would try tweaking "hinting" in the font settings, and I would try Windows fonts (be it Vista fonts or regular MS fonts). You could try the free Liberation font pack. You need to turn antialiasing on to smoothen your fonts. But uninstall the Sharpfonts tweak, as thuis is not what you are looking for ;)

---

### Post by toejamfootball on 2009-03-18
Ok I will try this. I am pretty certain I followed this How to the first time around though, and got that first screenshot.... *shrugs*

---

### Post by toejamfootball on 2009-03-18
Well, I am not having any luck. I guess I will put up with these blurry fonts for a while. Maybe what I did previously will come back to me, I know to write everything down now haha. Thanks for you help.

---

### Post by calande on 2009-03-18
Your distro should already provide smooth fonts like in Windows Vista or ClearType, with clean shapes. Most do...

---

### Post by toejamfootball on 2009-03-20
I gave up in my search for my previous settings. I have installed Ubuntu now over Xubuntu and am liking the fonts just fine how they are.

Thanks again for the help.

---

### Post by calande on 2009-03-21
@toejamfootball: FYI, I chose smooth fonts on my Gnome desktop (Intrepid Ibex), installing the Liberation font package, then I went to "System > Preferences > Appearance". I clicked the "Fonts" tab, selected Liberation fonts for the different drop-down menus. I selected "Subpixel smoothing (LCD)" for font rendering. In "Details", I selected "Hinting slight" and RGB". See attached screenshot. This is *not* the sharpfonts rendering, but it's still nice.

---

### Post by deviant78 on 2009-03-22
Easiest way I found was to backup all my TFF fonts from a Windows installation to a disc, then in home folder create a folder called .fonts, pasting the fonts in there.

They are now available to select, I find Segoe UI a good font.

Also enable subpixel smoothing for LCD screens.

---

### Post by calande on 2009-03-22
@deviant78: Yes, but not everybody has Windows (let alone Vista!). And in this case, you don't have sharpfonts, you have smooth fonts (like ClearType).

---

### Post by patocardo on 2009-04-12
> Make sure your /etc/apt/sources.list has these lines.

How I am supposed to make sure of that. What do I have to do?

---

### Post by juanbretti on 2009-04-12
> **patocardo said:**
> How I am supposed to make sure of that. What do I have to do?
What do you want to add to the "/etc/apt/sources.list"

Try running this command (Press Alt+F2): 

```
sudo gedit /etc/apt/sources.list
```

---

### Post by n0_mad on 2009-06-09
Hi, i made changes from first post and all fonts perfect but some of them very blocky. Is possible to make them smooth like others?

---

### Post by croash on 2009-06-19
Nice! now how do i disable?

---

### Post by IronArjen on 2009-07-02
The second seems appealing It works...........and it sucks bigtime (hence appalling). If you agree just uninstall the microzoft file and remove the four confs from your etc/fonts, logout and in and OK

---

### Post by fabdango on 2009-07-23
This messed my whole font config and there's no way of putting it back to default. I get:

```
 Fontconfig error: Cannot load default config file
```And it's all over.

Anyone knows a way to restore the default settings? And it's not like just deleting the files. It won't do.

Thanks.

---

### Post by iClouseau88 on 2009-07-24
How come you introduced "nicefonts.tbz" all of a sudden, whereas you had "fontconfig.tbz" before?  How do I get this "nicefonts.tbz" file, because I got an error saying: tar: nicefonts.tbz  No such file or folder?

Another error message: /etc/fonts : No such file or folder

I read the instruction from page 1 to page 5 several times!

---

### Post by iClouseau88 on 2009-07-25
PROBLEM SOLVED!

Nicefonts.tbz is just a joke. I retried the original solution and used "fontconfig.tbz" instead.  However, I was not too thrilled with "msttcorefonts".  I found that Segoe UI is a much better font.  I downloaded and extracted it to my Desktop, then sudo nautilus, then dragged the 2 Segoe UI ttf files over to the nautilus-opened desktop, put them in /usr/share/fonts folder.  The link and original instruction is in [http://ubuntusite.com/fix-get-best-firefox-font-linux/](http://ubuntusite.com/fix-get-best-firefox-font-linux/)

Now I am quite happy!  I am using this new Segoe UI fonts on my Linux Mint laptop!

;-))

---

### Post by m_ad on 2009-08-02
> **croash said:**
> Nice! now how do i disable?

:lolflag: I have the same question.. I like the new font config but in case I want to revert.. how do we?




Also, some of the text in firefox is a little blocky. I've messed with the hinting options under Fonts, but it doesn't seem to affect Firefox. Is there a way to fix this?

---

### Post by npss84 on 2009-09-22
Please some1 tell how to reverse, it looks really bad for me, and I can't do any changes at all in the appearance program... 

Thx

---

### Post by Szise on 2009-11-01
The idea, the size and type of the fonts are good, however still not good for eyes, must be improved to be used. Don't understand why other smart guys are not working to fix it, can be a revolution for our Ubuntu desktops. :(

---

### Post by corsakh on 2009-11-02
Works great, but Chromium is still using the old font. How do I change it?

ps Firerfox uses the new font.

---

### Post by Szise on 2009-11-03
Try the real Google Chrome browser: [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

---

### Post by DamitDan on 2009-11-08
I would just like to note that the simplest way to get the MS core fonts along with a bunch of other good things (flash, JRE, codecs) is through installing the "ubuntu restricted extras" package through Synaptic or Ubuntu Software Manager.

---

### Post by zika on 2009-11-08
> **DamitDan said:**
> I would just like to note that the simplest way to get the MS core fonts along with a bunch of other good things (flash, JRE, codecs) is through installing the "ubuntu restricted extras" package through Synaptic or Ubuntu Software Manager.Simplest way for getting MS fonts is installing ttf-mscorefonts-installer. You do not need a whole bunch of other stuff. Flash-plugin from ubuntu-restricted-extra is not 64-bit. There is newer jre also. It is always better to install one by one and choose the latest version. Just my $.01...

---

### Post by dooglo on 2009-12-02
> **calande said:**
> **[COLOR="DarkRed"]This tutorial now has a web site: [http://www.sharpfonts.com/](http://www.sharpfonts.com/)[/COLOR]** :)

I tweaked the fontconfig XML files so that fonts look like on Windows. This code is borrowed from [PC-BSD](http://www.pcbsd.org). First, let's install the Microsoft fonts. You have 2 ways of doing so:

Either download the [fonts](http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz) into your home directory and install them on your system:

```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```

Or, enable non-free, universe and multiverse repositories and install the Microsoft fonts:

```
sudo apt-get install msttcorefonts
```

You now have the Microsoft fonts installed. Let's configure your system now.

Download the [xml files]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz") and extract the file into /etc/fonts/ as root:

```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

Log out from Ubuntu and relog in. Here's how your desktop will look like:

[[IMG]http://img412.imageshack.us/img412/6972/ubuntu5ui.th.png[/IMG]](http://img412.imageshack.us/img412/6972/ubuntu5ui.png)

It's a lot more complex than disabling antialiasing at small font sizes :)

[SIZE="4"][DIGG IT!]("http://digg.com/linux_unix/Display_Microsoft_fonts_in_Unix_like_on_Windows")[/SIZE]



This is what I've been looking for.  I've downloaded XML files folder, but how do I extract them to the suggested foledr?

D.

---

### Post by dooglo on 2009-12-03
Bumpit bump bump

---

### Post by zika on 2009-12-03
> **dooglo said:**
> This is what I've been looking for.  I've downloaded XML files folder, but how do I extract them to the suggested foledr?

D.Read the third "code" in the message You've quoted.

---

### Post by haddog on 2010-04-02
> **Szise said:**
> Try the real Google Chrome browser: [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

Chromium browser fly's!

---

### Post by haddog on 2010-04-02
> **Szise said:**
> Try the real Google Chrome browser: [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

I use it more often than FF now...

---

### Post by admo on 2012-05-30
Those config files work in natty, but not in precise. How can I get fonts which look like in windows on ubuntu 12.04?

---

### Post by anoxi on 2013-05-03
This should work on newer Ubuntus:

```

cd /etc/fonts/conf.d
sudo wget https://launchpadlibrarian.net/59716493/39-clearfonts.conf
sudo dpkg-reconfigure fontconfig

```

---

### Post by matt_symes on 2013-05-03
Thanks for posting. 

However, as this is an old thread, i'll close it.

**Thread closed**

---

