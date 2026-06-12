---
title: "*notice* to Testers-Ubiquity has new layout!"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-07
@ Cariboo907

Could you let this one ride?  Thanks.

I just wanted to point out to CastroJo how some of the testers here might better be informed by changes that happene that we are not always imediately made aware of.

For example- the Ubiquity Installer now has +/-/and a cog wheel rather that the old layout. It has worked just fine with Beta 1 .

 My concern is that I was not aware that this change had taken place (although I have been reading some of kansanoobs msgs) . I just sort of stumbled upon it.

Cariboo907 mentioned something about being able to put up notices in the message forums when large changes like these are made. My suggestion is that perhaps we should follow-up on this.

@CastroJo

So this would be one of the things I think that could be of help to a lot of newer and veteran testers alike.

---

### Post by kansasnoob on 2012-09-07
I really wish those who are either effected, or are worried about how the new layout will effect new users, would comment at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I should point out though that the [newest proposal]("https://picasaweb.google.com/lh/photo/IX7RCztyVR5RU0OPsX2CXVh0btKKriD5FR8jiayHfxc?feat=directlink") replaces the "cog" with "Change" again but it leaves "+" and "-" as representative of Add and Delete.

My greatest fear is that someone will highlight a partition and click on "-" thinking it will reduce the size of the partition when it actually deletes the selected partition. As I said at the bug report:

> The symbolic icon "-" does NOT always mean "delete". In fact when you open the "change" dialogue to apply changes to a partition "-" clearly means reducing the size of the existing partition! This is true of many apps, typically "-" means shrink, lower, or reduce!

And it certainly does no good for me to just repeat what I see at the forums becausae the dev says;

> Ubuntu forums is self-selective and not representative.

---

### Post by ventrical on 2012-09-07
> **kansasnoob said:**
> I really wish those who are either effected, or are worried about how the new layout will effect new users, would comment at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799)

I should point out though that the [newest proposal]("https://picasaweb.google.com/lh/photo/IX7RCztyVR5RU0OPsX2CXVh0btKKriD5FR8jiayHfxc?feat=directlink") replaces the "cog" with "Change" again but it leaves "+" and "-" as representative of Add and Delete.

My greatest fear is that someone will highlight a partition and click on "-" thinking it will reduce the size of the partition when it actually deletes the selected partition. As I said at the bug report:



And it certainly does no good for me to just repeat what I see at the forums becausae the dev says;


 I hear you kansasnoob. But that was not the spirit of why I made this post. I made this post as a template/example so that we could have a better 'heads-up' because  some msgs  headings are very obscure and not definitive.Part of the problem is that we are always forking over to some other link (launchpad) when perhaps the problem can be dealt with here.

Also , a lot of us do not always have the 'proposed' repos enabled. "Choices" I guess ?

   Apparently it appears as if I have high-jacked your topic!? Not so.. but , out of respect I'll not deal with this matter any longer.

 Best Regards,

ventrical

---

### Post by kansasnoob on 2012-09-07
> Apparently it appears as if I have high-jacked your topic!? Not so.. but , out of respect I'll not deal with this matter any longer.


I didn't think you were hijacking at all :)

I think you misunderstood me, not surprising because my thought process even confuses me sometimes ;)

My point really is that if any of us think some feature in an important app such as the installer is confusing enough to require explanation to the testing community, then it would seem we could expect total noobs to be even more confused when the final release becomes available.

And IMHO if the installation process is at all confusing to any segment of the community that is a serious design flaw, and for the most part the only way to get a design flaw fixed is through Launchpad by filing a bug.

In this case a bug had been filed so I just joined in and tried to present the most relevant info I could, even stressing the point (perhaps too strongly) that I've dealt with ubiquity problems in the past and actually witnessed thru these forums the anguish of a user losing data or an existing OS.

But my concerns regarding "-" being mistaken for "reduce" rather than "delete" are being poo-poo'ed, so there is no more I can add to the conversation. Unless other testers join in the conversation at Launchpad that's it - done will be done - period!

Sure, once you know that "-" in that screen means "delete" you'll be fine, but if you use the very next screen to edit a partition "-" does absolutely mean "reduce" so it's confusing and IMHO a serious design flaw!

---

### Post by mips on 2012-09-07
> **kansasnoob said:**
> 
My greatest fear is that someone will highlight a partition and click on "-" thinking it will reduce the size of the partition when it actually deletes the selected partition.

They will probably only catch on when people start spewing fire after losing a partition. Let it roll & see how it pans out ;)

---

### Post by mc4man on 2012-09-07
I would guess due to current popularity of sym icons it's selected picking from the referenced design docu which did specify  - + ect.
Though it also did call for a confirmation alert  on deleting not empty or  not swap partitions
(and "accessible label "Delete This Partition", whatever that means, - tooltip?

---

### Post by grahammechanical on 2012-09-07
So, what we can do, I suppose, is either add our views to bug report 1045799 or when a user posts on the forum that they have mistakenly deleted a partition because of misunderstanding what "-" did, we direct them to bug report 1045799 with the suggestion that there is the place to record their experiences.

We could also do both. I have made a note of this bug number for future reference. I have just this minute burned beta 1. I will try it out tonight or tomorrow. Fingers crossed (as always) that I do not install into the wrong partition.

Regards.

---

### Post by jbicha on 2012-09-07
> **mc4man said:**
> 
(and "accessible label "Delete This Partition", whatever that means, - tooltip?

That's not the same as a tooltip. The "indicator" status menus all have accessible labels for screen readers and such, but do not have tooltips.

---

### Post by mc4man on 2012-09-07
> **jbicha said:**
> That's not the same as a tooltip. The "indicator" status menus all have accessible labels for screen readers and such, but do not have tooltips.
That makes more sense (accessibility

---

### Post by kansasnoob on 2012-09-07
> **grahammechanical said:**
> So, what we can do, I suppose, is either add our views to bug report 1045799 or **[COLOR="Red"]when a user posts on the forum that they have mistakenly deleted a partition because of misunderstanding what "-" did[/COLOR]**, we direct them to bug report 1045799 with the suggestion that there is the place to record their experiences.

We could also do both. I have made a note of this bug number for future reference. I have just this minute burned beta 1. I will try it out tonight or tomorrow. Fingers crossed (as always) that I do not install into the wrong partition.

Regards.

After a **new user** loses data inadvertently do you think they'll stick around long enough to create a Launchpad account and add a comment?

They'll likely just never look at Ubuntu again!

I don't remember who it was, but during one of these struggles another forum member said (paraphrasing), **"We want to convince people to throw Windows out of their computers, not convince them to throw their computers out the window"!**

With the newest spec (which is not yet available through the repos) the only apparent things that have changed on that screen are the replacement of Add and Delete with "+" and "-":

[ATTACH]223817[/ATTACH]

Yes, they're replacing the "gears/cog" icon with "Change" so that leaves only "+" replacing "add" and "-" replacing "delete".

That may seem fine to some people but when I test I always put my NOOB shoes on! Heck I think I could install Ubuntu with a fork and a spoon, but we NEED to be concerned about "virgin" users!

---

### Post by kansasnoob on 2012-09-07
> **mips said:**
> They will probably only catch on when people start spewing fire after losing a partition. Let it roll & see how it pans out ;)

Been there and done that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

With that track record how can [bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") ever be tackled :confused:

---

### Post by ventrical on 2012-09-07
@kansasnoob,

 Yes .. you are absolutely correct.

thank-you

regards,

ventrical

---

### Post by randomizer101 on 2012-09-07
I just don't think it makes sense to leave just two symbolic buttons in the UI when all the rest have text labels. It's inconsistent and unnecessary. Either make them all ambiguous symbols or make them all have text labels that describe what the button does.

---

### Post by kansasnoob on 2012-09-07
Well, in fairness lets be sure and look at these changes in the upcoming daily builds:

> ubiquity (2.11.31) quantal; urgency=low

  [ Colin Watson ]
  * Buffer reads from debconf-copydb. Python 3 defaults to unbuffered reads
    from byte streams, which is much slower.
  * Port oem-config-remove-gtk to Python 3, now that
    python3-aptdaemon.gtk3widgets exists; the final piece!
  * Remove Python 2 support. We aren't going back now.
  * Remove the rest of the long-dead PS3 port.

  [ Dmitrijs Ledkovs ]
  * Allow going from the encryption key setup page, to the disk space
    allocation page. (LP: #1046323)
  * Correctly apply styles to the title & progress sections and not the
    centre piece. This means themes are no longer required to provide non
    standard @dark_[fb]g_color colors, instead 'menubar' Gtk CSS style is
    used. This also fixes long standing a11y issues in HighContrast themes
    & requirements for non-standard color definitions. (LP: #744283)
  * Make lables in the segmented bar use the same colours as normal labels.
  * [B][COLOR="Red"]Changing the "Add/Remove/Change Partiontion" buttons to mixed
    symbolic/text buttons should make the screen comply with Ubiquity
    Design spec ( [http://goo.gl/Kokw5](http://goo.gl/Kokw5) ) and address confusion about the
    updated screen.[/COLOR][/B] (LP: #1045799)
  * Fix the disappearance of crypto password field (LP: #1045716)
  * Fix misallignment of crypto password fields (LP: #1045712)
  * Make setup security key page go back to ask page (LP: #1045698)
  * Remove powerpc/ps3 low-memory profile, as it doesn't do anything any
    more. gnome-session-remove command is no longer present, and the init
    processes it tried to stop no longer exist under those names. We do
    want a low memory profile, which ubiquity-only mode now.
  * ubiquity-wrapper: Add support for udisks2 inhibit, drop devkit-disks
    inhibit. (LP: #719338)
  * Prevent progress label to expand & shrink the window (LP: #1046241)
  * Automatic update of included source packages: base-installer
    1.122ubuntu9.

  [ Dylan McCall ]
  * Fixed slideshow_get_available_locale missing new locales in
    extra_slides_dir. (LP: #1046511)
 -- Dmitrijs Ledkovs <dmitrij.ledkov@ubuntu.com> Sat, 08 Sep 2012 00:47:54 

According to the design spec:

[https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.24217cfde395](https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.24217cfde395)

[ATTACH]223850[/ATTACH]

> If the partition is not known to be empty ... removing it should involve a confirmation alert .......

So lets see if it truly does that ;)

---

### Post by jerrylamos on 2012-09-08
> **ventrical said:**
> @ Cariboo907
 changes that happene that we are not always imediately made aware of.

For example- the Ubiquity Installer now has +/-/and a cog wheel rather than the old layout. It has worked just fine with Beta 1 On 3 beta 1 installs with manual partitioning + - @ didn't get me the drop down so I could set ext4 partition size (no change) format /.  A fast double click on the partition worked for the netbook and notebook.  With my 3.3 ghz tower no way could I double click fast enough.  The + - @ didn't get me the drop down like the previous change button would.

So I did an update while booted live then the manual partition double click worked.  Boring, because after install I had to do the same update all over again.  Anyway if someone is having trouble with beta 1 ubiquity try an update while booted live.  Worked for me.

---

### Post by grahammechanical on 2012-09-08
@kansasnoob

I agreee with you entirely about this comment:

> After a new user loses data inadvertently do you think they'll stick around long enough to create a Launchpad account and add a comment?

And yet bug reporting is the expected method of getting information to the developers and from comments made from time to time it seems that the developers do not always pay attention to bug reports and not are not likely to listen to us on Ubuntu+1.

They need to see for themselves the results of their decisions.

Regards.

---

### Post by ventrical on 2012-09-08
> **jerrylamos said:**
> On 3 beta 1 installs with manual partitioning + - @ didn't get me the drop down so I could set ext4 partition size (no change) format /.  A fast double click on the partition worked for the netbook and notebook.  With my 3.3 ghz tower no way could I double click fast enough.  The + - @ didn't get me the drop down like the previous change button would.

So I did an update while booted live then the manual partition double click worked.  Boring, because after install I had to do the same update all over again.  Anyway if someone is having trouble with beta 1 ubiquity try an update while booted live.  Worked for me.

 Iv'e done 2 installs on the same machine.  One, a side by side and the other a <something else> The Cog worked just great for me. Thanks for sharing your work-a-round. I had to do similar with Beta1 Precise I believe. It seems like all of your hardware is up to date and current. Definitely something with Ubiquity.

Just a side note- I now use "discard on shutdown" option when I use Startup Disk Creator . This has been a great helper because there always seemed to be some sort of deprecation to the USB stick after the first install with a persistive drive
on some machines.

---

### Post by jerrylamos on 2012-09-08
> Colin Watson: Changing the "Add/Remove/Change Partiontion" buttons to mixed symbolic/text buttons should make the screen comply with Ubiquity Design spec ( [http://goo.gl/Kokw5](http://goo.gl/Kokw5) ) and address confusion about the updated screen. (LP: #1045799) Now I know development design spec and developers are on a different planet.  Development doesn't read this forum so they won't see the "confusion" posts we make.  I haven't bothered to enter launchpad bugs on the + - @ which don't work for me since development isn't interested.  Not worth my while.  

What did work was fast left double click on the desired manual partition, although on my 3.3 gHz tower I had tu do a apt-get update apt-get dist upgrade to the live environemnt for the double click to work. I've posted that trick elsewhere sometimes people don't read every thread.

---

### Post by kansasnoob on 2012-09-08
> **grahammechanical said:**
> @kansasnoob

I agreee with you entirely about this comment:



And yet bug reporting is the expected method of getting information to the developers and from comments made from time to time it seems that the developers do not always pay attention to bug reports and not are not likely to listen to us on Ubuntu+1.

They need to see for themselves the results of their decisions.

Regards.

That's what I was trying to stress in the related bug report, albeit too harshly at first, but I'm blown away by the comment:

> Ubuntu forums is self-selective and not representative.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/15](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1045799/comments/15)

I'd say that these forums are very representative of the real life impact of design & development decisions ;)

BTW does anyone know how to open [this document]("https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1") in plain text so I can copy-n-paste sections of it instead of having to type whole sections like shown here:

[http://ubuntuforums.org/showpost.php?p=12225058&postcount=14](http://ubuntuforums.org/showpost.php?p=12225058&postcount=14)

I'll use the actual printed design spec as a bug fighting tool when I can :biggrin:

---

### Post by ventrical on 2012-09-08
I tried to get that .doc for you but no way I can select, copy or paste it. Not even in Libre.

---

### Post by ventrical on 2012-09-08
@kansasnoob

                                                "Ubuntu forums is self-selective and not representative.                      "

It is probably why most of the older relic bugs and infrastructures never got re-built, because of this attitude. IF a particular dev is going to put himself in a fishbowl and subject his program to Turing Machines only, then the results are , of course, going to be what we are seeing now. It's like , they don't trust us and we don't trust them. 

We have to keep at these bugs, but, more importantly,  there are some devs who really appreciate our help. Can I name one ? No .. but I have to assume on the good natured concept of Ubuntu that they just do.

---

### Post by vasa1 on 2012-09-08
> **ventrical said:**
> I tried to get that .doc for you but no way I can select, copy or paste it. Not even in Libre.
I managed to open it using Seamonkey and then save it to disk. I can now view it off-line. But, as you guys found, it's pretty impossible to extract anything from it.
Quite an unfriendly format.

Edit: the figures are stored in a separate folder.

---

### Post by kansasnoob on 2012-09-08
> there are some devs who really appreciate our help. Can I name one ?

I've actually worked with a few that showed excellent appreciation. Colin Watson is #1! But there are others.

---

### Post by kansasnoob on 2012-09-08
> **vasa1 said:**
> I managed to open it using Seamonkey and then save it to disk. I can now view it off-line. But, as you guys found, it's pretty impossible to extract anything from it.
Quite an unfriendly format.

I'm going out to beat the crap out an old tractor but when I'm done I guess I need to start making screenshots of that whole document so I can prove that many installer decisions;

(a) actually violate the design specs some devs like to hold up as their reasoning for changes

and,

(b) some decisions are made totally off-the-cuff, such as deciding to drop the option to "install in largest free space".

I have a huge file full of bookmarks beginning with Maverick that I can use to prove that even Colin Watson (the head of the installer team) agrees with me 90% of the time on required changes but his hands are tied :mad:

---

### Post by vasa1 on 2012-09-08
For what it's worth, I put the text up over here:
[https://docs.google.com/open?id=0B4gs9P5_zkged0xLSDlrNmJ5eUE](https://docs.google.com/open?id=0B4gs9P5_zkged0xLSDlrNmJ5eUE)
I'll keep it there for a couple of days.
It's messy but ...

---

### Post by kansasnoob on 2012-09-08
> **vasa1 said:**
> For what it's worth, I put the text up over here:
[https://docs.google.com/open?id=0B4gs9P5_zkged0xLSDlrNmJ5eUE](https://docs.google.com/open?id=0B4gs9P5_zkged0xLSDlrNmJ5eUE)
I'll keep it there for a couple of days.
It's messy but ...

Every effort is worthwhile :)

I'll save that.

---

### Post by vasa1 on 2012-09-08
> **kansasnoob said:**
> Every effort is worthwhile :)

I'll save that.
I did it this way ... First, I opened the link in Firefox and let the document load completely. Then, I saved using "web page complete". Then, I reopened the html file which I saved to my desktop, again with Firefox and didn't bother about the images but this time chose to save as "text only". And that's what I uploaded.

I'm mentioning this because the document may be revised in the days to come. And you may want to save the text of future versions.

---

### Post by vasa1 on 2012-09-08
> **kansasnoob said:**
> ...
According to the design spec:

[https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.24217cfde395](https://docs.google.com/a/canonical.com/document/preview?id=1bZ4yQIVgGaUGSYu3qiUHnQt3ieBZoqunP_DcleHCr3I&pli=1#heading=h.24217cfde395)
...

What informational value does the blue ribbon convey? (Somethings are tagged; others aren't.)

---

### Post by kansasnoob on 2012-09-09
> **vasa1 said:**
> What informational value does the blue ribbon convey? (Somethings are tagged; others aren't.)

No idea :confused:

---

### Post by vasa1 on 2012-09-09
@kansasnoob,
re. this google doc, I find that it displays differently in Firefox, Opera and Seamonkey than it does in Chrome.

In the first bunch of browsers, there's at least one part that's messed up (at least for me).

The two images are for Firefox  and for Chrome.

Filed [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1048276").

---

### Post by kansasnoob on 2012-09-09
Well I did some more testing with Ubuntu i386 20120908 and it does seem better, but it's important to remember that I now know "-" is synonymous with "delete" in that particular screen of the manual partitioner.

It's also important to note that "-" does mean "reduce" if using the "Change" dialogue in ubiquity, so it's just nonsense to argue that "-" is always synonymous with "delete" since the use of "-" is used by the same app (ubiquity) to mean "reduce the size of this partition"!  

I can also point out many other places where "-" means "reduce" or "lower" in other apps, particularly in desktop environments other than Gnome.

Regardless here's how it looks. I used my test partition /dev/sda18 which had been used for an OO -> PP upgrade during 12.04.1 testing:

[ATTACH]223922[/ATTACH]

You can see there that sda18 is selected and it shows 4911 MB used. The actions "-", change, and revert are active. So I click on "-":

[ATTACH]223923[/ATTACH]

Now I have free space displayed where sda18 used to be, and only New Partition Table and Revert are displayed since the partitioner auto-displays the entire disc so I click on Revert:

[ATTACH]223924[/ATTACH]

So on one hand I think we're OK, but OTOH I just can't get past the fact that "-" does NOT always mean Delete!

Also the design spec says,

[ATTACH]223925[/ATTACH]

Are we displaying adequate warning that a partition containing data may be deleted??????????????

I think we're lacking the "confirmation" called for by that design spec!

---

### Post by jerrylamos on 2012-09-09
Colin Watson is enamored with the +-@ so we're stuck with it.  I much appreciate this forum warning us testers about the danger posed by inadequately explained hazards.

For whatever reason I've avoided using +-@ destruction by very fast double left click on the desired partition.  I assume they'll remove that option.

Somehow Ubiquity always assumes I want to delete or shrink or grow a partition.  So far for the last 6 years I've been able to just use the selected partition which I would think would be the default, obviously I don't understand their thinking.  

With the LARGE hard drives today we have lots of stuff on the hard drive and do not want to destroy what we have.  Somebody else can test the other install options....

---

### Post by kansasnoob on 2012-09-09
Maybe almost off-topic, but since we're eliminating the alt images it's worth mentioning that the alt's had a very clear option to "Use largest continuous free space" but the live installer does NOT!

The history behind that is long and painful, beginning with Maverick, but even Colin Watson had this to say during PP dev:

> I would like to redesign this for Q, since it's come up several times as a problem. However, it's been this way for a few releases, and we aren't going to be able to do anything about it for 12.04 at this point.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/7](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/7)

I'm getting old and tired but I still haven't totally lost my mind :lolflag:

How close is the live installer to the principle that;

> The Ubuntu Live CD is the first experience many new users will have of Ubuntu. The installation experience
should be attractive and effortless to reassure new users that Ubuntu is the right choice. The process should
feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).
The installation process should support the following types of user:
1.Users with no prior knowledge of Ubuntu or understanding of the nature of an operating system
2.Users who already know they want to install Ubuntu
3.Expert Ubuntu users who have very specific configuration requirements.

---

### Post by kansasnoob on 2012-09-09
> **jerrylamos said:**
> **[COLOR="Red"]Colin Watson is enamored with the +-@ so we're stuck with it.[/COLOR]**  I much appreciate this forum warning us testers about the danger posed by inadequately explained hazards.

For whatever reason I've avoided using +-@ destruction by very fast double left click on the desired partition.  I assume they'll remove that option.

Somehow Ubiquity always assumes I want to delete or shrink or grow a partition.  So far for the last 6 years I've been able to just use the selected partition which I would think would be the default, obviously I don't understand their thinking.  

With the LARGE hard drives today we have lots of stuff on the hard drive and do not want to destroy what we have.  Somebody else can test the other install options....

Where do you get that info/opinion?

I've not seen Colin comment on any of those bugs.

---

### Post by kansasnoob on 2012-09-09
@ Jerry,

Maybe you're misreading which dev did what:

> ubiquity (2.11.31) quantal; urgency=low

[ Colin Watson ]
* Buffer reads from debconf-copydb. Python 3 defaults to unbuffered reads
from byte streams, which is much slower.
* Port oem-config-remove-gtk to Python 3, now that
python3-aptdaemon.gtk3widgets exists; the final piece!
* Remove Python 2 support. We aren't going back now.
* Remove the rest of the long-dead PS3 port.

[ Dmitrijs Ledkovs ]
* Allow going from the encryption key setup page, to the disk space
allocation page. (LP: #1046323)
* Correctly apply styles to the title & progress sections and not the
centre piece. This means themes are no longer required to provide non
standard @dark_[fb]g_color colors, instead 'menubar' Gtk CSS style is
used. This also fixes long standing a11y issues in HighContrast themes
& requirements for non-standard color definitions. (LP: #744283)
* Make lables in the segmented bar use the same colours as normal labels.
* Changing the "Add/Remove/Change Partiontion" buttons to mixed
symbolic/text buttons should make the screen comply with Ubiquity
Design spec ( [http://goo.gl/Kokw5](http://goo.gl/Kokw5) ) and address confusion about the
updated screen. (LP: #1045799)
* Fix the disappearance of crypto password field (LP: #1045716)
* Fix misallignment of crypto password fields (LP: #1045712)
* Make setup security key page go back to ask page (LP: #104569
* Remove powerpc/ps3 low-memory profile, as it doesn't do anything any
more. gnome-session-remove command is no longer present, and the init
processes it tried to stop no longer exist under those names. We do
want a low memory profile, which ubiquity-only mode now.
* ubiquity-wrapper: Add support for udisks2 inhibit, drop devkit-disks
inhibit. (LP: #71933
* Prevent progress label to expand & shrink the window (LP: #1046241)
* Automatic update of included source packages: base-installer
1.122ubuntu9.

[ Dylan McCall ]
* Fixed slideshow_get_available_locale missing new locales in
extra_slides_dir. (LP: #1046511)
-- Dmitrijs Ledkovs <dmitrij.ledkov@ubuntu.com> Sat, 08 Sep 2012 00:47:54 

Dmitrijs Ledkovs is the one that's applied these latest changes, and he's the one that I've been butting heads with. But I was inappropriate with my earliest criticism, and I've therefore "muddied the waters" to the point that I'm probably no longer effective.

---

### Post by kansasnoob on 2012-09-09
> **kansasnoob said:**
> Maybe almost off-topic, but since we're eliminating the alt images it's worth mentioning that the alt's had a very clear option to "Use largest continuous free space" but the live installer does NOT!

The history behind that is long and painful, beginning with Maverick, but even Colin Watson had this to say during PP dev:



[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/7](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/964331/comments/7)

I'm getting old and tired but I still haven't totally lost my mind :lolflag:

How close is the live installer to the principle that;

Just thought to add, this does go back to here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

And it had a timeline to be fixed, but rather than fixing bugs it seems the designers decided we should break more things.

---

### Post by ventrical on 2012-09-09
> **jerrylamos said:**
> 

With the LARGE hard drives today we have lots of stuff on the hard drive and do not want to destroy what we have.  Somebody else can test the other install options....

  And for this reason I am apprehensive to do partition installs on some of my larger machines. I do run LIVE tests from USBs to test NVidia, etc.. but I  have made one 1/2 terabyte hdd setup for rolling releases only.

 Then, on the otherside of the coin ,  the partition manager  in Ubiquity has literally resurrected ophaned machines designated for the recycle bin. It's worth it's weight in gold.

---

### Post by jerrylamos on 2012-09-09
> **kansasnoob said:**
> Where do you get that info/opinion?
I've not seen Colin comment on any of those bugs.You're right.  After Colin's comments there is:>  Dmitrijs Ledkovs ]
* Allow going from the encryption key setup page, to the disk space
allocation page. (LP: #1046323)
* Correctly apply styles to the title & progress sections and not the
centre piece. This means themes are no longer required to provide non
standard @dark_[fb]g_color colors, instead 'menubar' Gtk CSS style is
used. This also fixes long standing a11y issues in HighContrast themes
& requirements for non-standard color definitions. (LP: #744283)
* Make lables in the segmented bar use the same colours as normal labels.
* Changing the "Add/Remove/Change Partiontion" buttons to mixed
symbolic/text buttons should make the screen comply with Ubiquity
Design spec ( [http://goo.gl/Kokw5](http://goo.gl/Kokw5) ) and address confusion about the
updated screen. (LP: #1045799)I missed the author change.  I'm not familiar with Dmitrijs.  Perhaps he isn't confused I think some of us are....

---

### Post by ventrical on 2012-09-09
> **kansasnoob said:**
> Well I did some more testing with Ubuntu i386 20120908 and it does seem better, but it's important to remember that I now know "-" is synonymous with "delete" in that particular screen of the manual partitioner.

It's also important to note that "-" does mean "reduce" if using the "Change" dialogue in ubiquity, so it's just nonsense to argue that "-" is always synonymous with "delete" since the use of "-" is used by the same app (ubiquity) to mean "reduce the size of this partition"!  

I can also point out many other places where "-" means "reduce" or "lower" in other apps, particularly in desktop environments other than Gnome.

Regardless here's how it looks. I used my test partition /dev/sda18 which had been used for an OO -> PP upgrade during 12.04.1 testing:

[ATTACH]223922[/ATTACH]

You can see there that sda18 is selected and it shows 4911 MB used. The actions "-", change, and revert are active. So I click on "-":

[ATTACH]223923[/ATTACH]

Now I have free space displayed where sda18 used to be, and only New Partition Table and Revert are displayed since the partitioner auto-displays the entire disc so I click on Revert:

[ATTACH]223924[/ATTACH]

So on one hand I think we're OK, but OTOH I just can't get past the fact that "-" does NOT always mean Delete!

Also the design spec says,

[ATTACH]223925[/ATTACH]

Are we displaying adequate warning that a partition containing data may be deleted??????????????

I think we're lacking the "confirmation" called for by that design spec!

Those gadgets absolutely should have hover dialog boxes with the pertinent info in them. This goes back to 'Linux for Human Beings'.  Someone should point this out to Mark Shuttleworth. I do not know of any other way to make a case to the developers. For me, I caught on real quick.. I just instinctively knew what they meant (years of experience) but with noobs  it is a whole different story.

---

### Post by kansasnoob on 2012-09-10
Just adding a note here for my own future use:

> Second, a “–” button (with accessible label “Delete This Partition”), sensitive whenever the currently selected
area is a partition in that chart. If the partition is not known to be empty or swap, [B]removing it should involve a
confirmation alert of the form ‘The partition “{id}” contains {amount} of data. Are you sure you want to delete
it?’ or ‘The partition “{id}” may contain data. Are you sure you want to delete it?’[/B].

I don't believe this is happening :(

---

### Post by ventrical on 2012-09-10
No , it is not happening. I just did the daily.  It is beggining to become a real embarassment.

---

### Post by kansasnoob on 2012-09-13
I've been trying my best to watch launchpad for new ubiquity bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?orderby=-datecreated&start=0](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?orderby=-datecreated&start=0)

And I see that *guitara* has reported a couple:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050044](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050044)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050562](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050562)

I find both of those very interesting and I truly hope Canonical will leave Nicholas on the job long enough to address some of the confusing options offered by the live installer :)

I'll try to address each bug separately very soon, I took some screenshots just yesterday but I've been too busy to do anything with them :(

I also found this one to be very important:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1049549](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1049549)

I think it makes perfect sense that grub should NOT be installable to any partition containing Win boot files.

---

