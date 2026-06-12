---
title: "ThunderBird 2 Feisty"
date: 2007-04-19
forum: Repositories &amp; Backports
---

### Post by daniel of sarnia on 2007-04-19
Hello, today Thunderbird 2 was released. Does anyone know if it is going to be back ported to feisty? If so, when can it be expected?

---

### Post by zachtib on 2007-04-19
I've been trying to build a feisty deb of this all day long.  The problem is, Thunderbird doesn't want to compile properly on feisty even if just using make.

---

### Post by testube_babies on 2007-04-20
I always keep this script handy (it installs the latest version of thunderbird):

[http://pykeylogger.sourceforge.net/installnewthunderbird.sh](http://pykeylogger.sourceforge.net/installnewthunderbird.sh)

---

### Post by daniel of sarnia on 2007-04-20
I've just been using the pre-compiled i686 from Mozilla, I suppose if it's not back ported I'll give up next weekend to trying to build a deb unless you or someone else does it first, which would be highly appreciated! But for tonight I still have homework to finish. 

If anyone knows if it is going to be back ported I'd be grateful for an ETA on that.:)

---

### Post by daniel of sarnia on 2007-04-20
> **testube_babies said:**
> I always keep this script handy (it installs the latest version of thunderbird):

[http://pykeylogger.sourceforge.net/installnewthunderbird.sh](http://pykeylogger.sourceforge.net/installnewthunderbird.sh)

Should we be worried that that file comes from a site called pyKEYLOGGER.sourceforge.net :confused: :confused:

---

### Post by Billy McCann on 2007-04-20
It's the same script [here](https://help.ubuntu.com/community/ThunderbirdNewVersion), which sits pretty comfortably with me.  :KS

---

### Post by limaunion on 2007-04-22
+1 vote for backporting Thunderbird!

---

### Post by wyth on 2007-04-22
Backport this thing, so's we can install Lightning and sync it up with Google Calendar (the Provider addon only works with 2.0).

---

### Post by JMO707 on 2007-04-22
> **wyth said:**
> Backport this thing

Please, please??

---

### Post by Tanker Bob on 2007-04-22
> **JMO707 said:**
> Please, please??
Please, please, please???

---

### Post by beerfan on 2007-04-22
In the meantime, just download the Mozilla binary and install it in your home dir.

[http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/)

I use /home/beerfan/bin/thunderbird

---

### Post by kolinab on 2007-04-22
Can one of you guys please explain to me what it means to backport something? I gather that it means putting the newer version in the repos or something, but other than easier installation, how does this provide better functionality? Or does it? Maybe I want T-bird backported too!

---

### Post by Tanker Bob on 2007-04-22
> **kolinab said:**
> Can one of you guys please explain to me what it means to backport something? I gather that it means putting the newer version in the repos or something, but other than easier installation, how does this provide better functionality? Or does it? Maybe I want T-bird backported too!
They contain software unsupported by the primary Ubuntu team and usually offers leading-edge updates not yet incorporated into the main Ubuntu repositories as well as fully-tested, released updates that won't officially appear until the next Ubuntu version release.  From the sources.list file:

```

# # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
# # team, and may not be under a free licence. Please satisfy yourself as to
# # your rights to use the software. Also, please note that software in
# # multiverse WILL NOT receive any review or updates from the Ubuntu
# # security team.
```

There can be lots of good stuff there, but it can carry higher risk in some cases.  Thunderbird 2.0 would not carry that risk.  You definitely want to see TBird there if the Ubuntu team won't put it in the main repositories.

---

### Post by kolinab on 2007-04-22
Thanks for the detailed reply Tanker Bob. OK, so now I know I want it backported!

---

### Post by beerfan on 2007-04-22
> **kolinab said:**
> Thanks for the detailed reply Tanker Bob. OK, so now I know I want it backported!

Canonical has historically been disinclined to backport newer versions of Mozilla apps. Dapper Drake, which is an LTS release, still has only Firefox 1.5 (unless I'm mistaken). However, maybe the fact that Feisty is not LTS and the fact that Thunderbird 2.0 was released literally the same day will encourage them to do so.

---

### Post by dennis1200 on 2007-04-22
The above script works fine, but is there an uninstall script as well? Probably should have looked for that prior to running the .sh

---

### Post by beerfan on 2007-04-22
> **dennis1200 said:**
> The above script works fine, but is there an uninstall script as well? Probably should have looked for that prior to running the .sh

For this reason, and to avoid interfering with the package system, it's best to install in your home directory as I suggested above.

---

### Post by Tanker Bob on 2007-04-22
I decompressed the .tar.gz file into my home directory and performed the redirection as laid out in the script, but TB 2.0 doesn't have sound nor does clicking on links in messages bring up the link in Firefox.  I closed 2.0 and opened 1.5 and the latter works fine.  All settings in the Preferences are correct.  Any ideas?

---

### Post by cruss on 2007-04-23
[URL="http://www.getautomatix.com/forum/index.php?showtopic=1029"]Automatix to the rescue?
[/URL]

The main reason that I want it from a repository is that when 2.0.0.1 comes out (and 2.0.1.4 for that matter) I not only get notified but I get it properly installed on top of my current install with no conflicts. If the "official backports repo" won't do it, lets encourage the community to step up.

---

### Post by iGama on 2007-04-23
Debian files of all Mozilla software.

[https://wiki.ubuntu.com/MozillaTeam/PreviewArchives](https://wiki.ubuntu.com/MozillaTeam/PreviewArchives)

Have fun

---

### Post by dnns on 2007-04-23
@iGama

The feisty repositories don't work anymore. Haven't tried the ones for edgy as i'm running 7.04. I think the link is outdated.

---

### Post by earobinson on 2007-04-23
I would love to see the new thunderbird

---

### Post by NJC on 2007-04-23
Add me to the list of wanting Tbird 2 in the repositories (backporting?). Not sure if I trust my skill to install it via tar file.

---

### Post by david.nqd on 2007-04-23
> **NJC said:**
> Not sure if I trust my skill to install it via tar file.

Sounds like the perfect reason to give it a try :) .

---

### Post by iGama on 2007-04-23
Like i said before:

Thunderbird 2.0 deb for feisty

[http://gnomefreak.youmortals.com/mozilla-testing/dists/feisty/main/binary-i386/thunderbird_1.99.release+2.0-2_i386.deb](http://gnomefreak.youmortals.com/mozilla-testing/dists/feisty/main/binary-i386/thunderbird_1.99.release+2.0-2_i386.deb)

---

### Post by NJC on 2007-04-23
> **david.nqd said:**
> Sounds like the perfect reason to give it a try :) .


Yes and No. Yes if I can pull it off successfully but No if I farg up our email. I'm going to give it a go since if I do banish it altogether during the install, I can always take temporary refuge in Tbird via dual boot Win. 

I think I'll try it in Linux via the tar file, I'll just uninstall Tbird first ... and backup my Profile directory 2nd!

---

### Post by beerfan on 2007-04-23
> **cruss said:**
> The main reason that I want it from a repository is that when 2.0.0.1 comes out (and 2.0.1.4 for that matter) I not only get notified but I get it properly installed on top of my current install with no conflicts. If the "official backports repo" won't do it, lets encourage the community to step up.

Actually, if you run the Mozilla build in your home directory, Thunderbird will update itself when the next update is released. If you run the Ubuntu package Thunderbird can't update itself and you'll be a week behind, at best, just like with Firefox. I'm not saying this as an argument against back-porting it but merely to point out that "getting update notification" isn't a good reason.

---

### Post by thornelawler on 2007-04-23
I concur very much: This would be a very cool thing.

One of Ubuntu's big drawcards for me is always that it does the bleeding edge thing. Missing a major release like this that happened on the same day as the Feisty release would be way sad.

---

### Post by dennis1200 on 2007-04-23
I would avoid the script posted above; mine crashed very frequently, and it was a bit of command line fixin' to get back to version 1.5. Fortunately I looked at the script and it wasn't too complicated in terms of where things where (essentially just a new /opt/thunderbird and /home/~user~/.thunderbird, along with a change in the /usr/bin filename. And preferred applications (make sure to change that back).

---

### Post by dfm21 on 2007-04-24
/vote yes
I humbly beg the overwhelming wise backporters to do what they can with Thunderbird 2...

---

### Post by Jhongy on 2007-04-24
+1 ^^^ What he said.

I want the simplicity of getting TB2 from the repos... don't want to have to deal with incompatibilities or things getting borked at the next upgrade.

---

### Post by garrido on 2007-04-24
Just spoke to the fine fellows at #ubuntu-mozillateam, and they are not sure yet if it will be available as a backport - apparently there is some issue with tbird2 requiring  libnspr (from what I gather some Mozilla library to handle multi-platform threading) and libnss (something to do with support for ssl and such), which are not available in Feisty.  You can add their repository, "deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main", but that will upgrade your Firefox too, which at least in my case broke my java plugin.

---

### Post by syxbit on 2007-04-24
you can just DL the thunderbird deb, without adding the repo to your sources.list

---

### Post by Megaqwerty on 2007-04-25
> **daniel of sarnia said:**
> Should we be worried that that file comes from a site called pyKEYLOGGER.sourceforge.net :confused: :confused:
Haha, I thought the same thing, so I read the whole script. It does a lot of stuff in preperation to make sure Thunderbird will work before it is installed, but does in fact install thunderbird. And as long as mozilla doesn't totally redesign the way their website is set up, this script will work in the future as well.

---

### Post by nanotube on 2007-04-25
> **daniel of sarnia said:**
> Should we be worried that that file comes from a site called pyKEYLOGGER.sourceforge.net :confused: :confused:

heh, no you shouldn't. i am the author of the script, and i also happen to be the author of pykeylogger (which is an open source python keylogger). so i just threw the script up on the website i already had. 

also, the install scripts now have a "new home", and we are doing some active improvements. check it out here:
[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

if anyone has suggestions for improvements, bug reports, etc, that's the place to go to help us out. :)

---

### Post by Romulus15 on 2007-04-25
@nanotube:
Hey,
simply want to thank you for the script. Nice work

---

### Post by Barrakketh on 2007-04-25
> **beerfan said:**
> Canonical has historically been disinclined to backport newer versions of Mozilla apps. Dapper Drake, which is an LTS release, still has only Firefox 1.5 (unless I'm mistaken). However, maybe the fact that Feisty is not LTS and the fact that Thunderbird 2.0 was released literally the same day will encourage them to do so.

I'm 95% sure the reason why Firefox 2 wasn't backported to Dapper is because it used a new version of Gecko, which other applications rely on.  Upgrading a package that it used as a dependency effectively disqualifies it as a backport candidate.

---

### Post by syxbit on 2007-04-25
Firefox 2 doesn't use a new version of Gecko.
it uses 1.8, just like FF 1.5 (and thunderbird 1.5, 2.0)

firefox/thunderbird 3.0 will use gecko 1.9

---

### Post by Barrakketh on 2007-04-25
> **syxbit said:**
> Firefox 2 doesn't use a new version of Gecko.
it uses 1.8, just like FF 1.5 (and thunderbird 1.5, 2.0)

firefox/thunderbird 3.0 will use gecko 1.9

[Bug #68158](https://bugs.launchpad.net/dapper-backports/+bug/68158) covers the reason.  Might not have been Gecko, but the reasoning still stands:

[quote=Martin Meredith]Hi there Douglas.

As John's stated, it's not possible to backport firefox without backporting a lot of different applications with it.

These applications depend on having certain versions of system libraries in certain places.

The way backports works is to update packages and replace them, not to have packages that work along side them.

Because of this it is impossible to backport firefox without backporting a massive chain of packages (188 packages to be precise)

I do not believe you will find any member of the backports team who is willing to do that.

**snip**[/quote]

---

### Post by durant1958 on 2007-04-25
Flawed reasoning.

It may be that it is a lot of work to backport Firefox 2 to dapper, however that is one of the aspects of Long Term Support.  You have to do something that you really really really don't want to do.

This refusal to support the LTS release caused me to dump Dapper in favor of SUSE 10.1.

---

### Post by nanotube on 2007-04-25
> **Romulus15 said:**
> @nanotube:
Hey,
simply want to thank you for the script. Nice work

you're welcome. :)

---

### Post by nanotube on 2007-04-25
> **durant1958 said:**
> Flawed reasoning.

It may be that it is a lot of work to backport Firefox 2 to dapper, however that is one of the aspects of Long Term Support.  You have to do something that you really really really don't want to do.

This refusal to support the LTS release caused me to dump Dapper in favor of SUSE 10.1.

that is a good point. a lot of people use our install scripts for firefox and thunderbird, precisely due to the fact that updated ff and tb are pretty essential packages. it would be simpler for all concerned if they updated the repositories packages...

but in the meantime, i encourage you to use the scripts. :)
our wiki site:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
our 3rd party project forum area:
[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by Tanker Bob on 2007-04-25
I tried the script, which executed fine, but Thunderbird 2.0's new mail sound didn't work, the hyperlinks in messages didn't, and other problems.  I'm running Feisty x86-64, so I'm wondering if there's an install setup for 64-bit systems.  I'm back using 1.5.0.10 because I couldn't get TB 2.0 to work correctly, although it would retrieve mail.

---

### Post by kiwinewt on 2007-04-26
I have the problem of no sound and links not working by using the tar file.

Another vote for it to be in the repo's.

And one for updates preferably sooner than a week...

---

### Post by luder on 2007-04-26
I'm running Feisty 64bits and I'm getting this error when I try to run thunderbird, after using the script:

/opt/thunderbird/run-mozilla.sh: line 166: /opt/thunderbird/thunderbird-bin: No such file or directory

---

### Post by nanotube on 2007-04-26
if your links don't open, can you check to see what you have in your System>preferences>preferred applications? the browser should be whatever you want to open your links.

don't know about the sound, though...

and luder, please post your output of:
```
ls -al /opt/thunderbird
```

also, everyone: please post questions/problems with the tbird script in the designated ubuntuzilla subforum, here:
[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

rather than coopt this backports thread. :)

---

### Post by nanotube on 2007-04-26
btw, i just noticed that you guys are using 64bit... not sure if it's even supposed to work. :) we haven't had any official testing of the script on 64bit ubuntu, and i'm pretty sure that the thunderbird tar.gz archive is compiled for 32bits...

---

### Post by Tanker Bob on 2007-04-26
The problem is not with the scripts or the default browser setting.  Apparently TB 2.0 needs libraries that aren't in the x86-64 setup.  Until TB 2.0 is put in the repository with all the dependencies resolved, the script won't help folks with a Feisty x86-64 distribution.

---

### Post by nanotube on 2007-04-26
> **Tanker Bob said:**
> The problem is not with the scripts or the default browser setting.  Apparently TB 2.0 needs libraries that aren't in the x86-64 setup.  Until TB 2.0 is put in the repository with all the dependencies resolved, the script won't help folks with a Feisty x86-64 distribution.

do you know what libraries those are? once we know, we could try to take care of the problems...

---

### Post by RawMustard on 2007-04-27
If you want links in thunderbird to work, just add these lines to your user created user.js file inside your .thunderbird profile.
```
user_pref("network.protocol-handler.app.ftp","/usr/bin/firefox");
user_pref("network.protocol-handler.app.http","/usr/bin/firefox");
user_pref("network.protocol-handler.app.https","/usr/bin/firefox");
```

If you link /usr/bin/thunderbird to  /opt/thunderbird/thunderbird then firefox can send mail links to thunderbird. And don't forget to set your prefered application to thunderbird :)

Works for me running feisty 64bit!

Honestly, this policy of not updating important apps like thunderbird, firefox and oppenoffice are pure bullshit.  The windows crowd are just laughing their butts off at this.  For they just download and install and away they go.  We have to live with old outdated crap, doesn't sound like such an advanced system this linux os huh? :-\"

Hope this helps some!

---

### Post by boborosso on 2007-04-27
> **durant1958 said:**
> Flawed reasoning.

It may be that it is a lot of work to backport Firefox 2 to dapper, however that is one of the aspects of Long Term Support.  You have to do something that you really really really don't want to do.

This refusal to support the LTS release caused me to dump Dapper in favor of SUSE 10.1.

I don't consider having bleeding edge packages as an aspect of LTS. And Novell "in bed with Microsoft" SUSE of all distros? Good luck with that. (Bias alert: i'm a debianist). 
 
Having said all that, if a backport requires a hundred dependencies backported too, why not making a static binary? Might work with debian too :)

---

### Post by Tanker Bob on 2007-04-27
> **RawMustard said:**
> If you want links in thunderbird to work, just add these lines to your user created user.js file inside your .thunderbird profile.
```
user_pref("network.protocol-handler.app.ftp","/usr/bin/firefox");
user_pref("network.protocol-handler.app.http","/usr/bin/firefox");
user_pref("network.protocol-handler.app.https","/usr/bin/firefox");
```

If you link /usr/bin/thunderbird to  /opt/thunderbird/thunderbird then firefox can send mail links to thunderbird. And don't forget to set your prefered application to thunderbird :)

Works for me running feisty 64bit!

Honestly, this policy of not updating important apps like thunderbird, firefox and oppenoffice are pure bullshit.  The windows crowd are just laughing their butts off at this.  For they just download and install and away they go.  We have to live with old outdated crap, doesn't sound like such an advanced system this linux os huh? :-\"

Hope this helps some!
Then how do we fix the lack of sound in TB 2.0?  When a sound should play, this error appears in the error console:

```

Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsISound.play]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://messenger/content/preferences/general.js :: anonymous :: line 141"  data: no]
```

---

### Post by RawMustard on 2007-04-27
Must be a bug in thunderbird, put in a bug report with mozilla crew!

---

### Post by Tanker Bob on 2007-04-27
> **RawMustard said:**
> Must be a bug in thunderbird, put in a bug report with mozilla crew!

Thanks.  Good luck--they couldn't be bothered to answer when I posted on the TB support forum.

---

### Post by beerfan on 2007-04-27
> **boborosso said:**
> I don't consider having bleeding edge packages as an aspect of LTS. And Novell "in bed with Microsoft" SUSE of all distros? Good luck with that. (Bias alert: i'm a debianist).

Bleeding edge? Since when is a final released version of a professional program "bleeding edge"? This may be an appropriate term in the typical open source world where people release first and ask questions later but it hardly applies to Firefox or Thunderbird.

As has already been stated, the issue is not with software maturity but with the deficiencies in the library dependency architecture. Perhaps when the GRE reaches maturity this issue will be minimized for Mozilla applications but somehow I expect other issues to step in and the place.

---

### Post by wilberfan on 2007-04-28
Well, I just used the Thunderbird script on my 64bit Feisty, and all seems well.   I DO get sound when new mail arrives...and adding swiftfox entries to the user.js file means that links open OK...

It IS a shame that it takes so long for new releases like this to make it to the repos.   I'm a BIG fan of Ubuntu (Feisty, especially) but openSUSE 10.2 seems to get releases like these almost immediately?

---

### Post by nanotube on 2007-04-29
by the way, you 64bit people have to have the ia32 libs installed in order to run the mozilla-build of thunderbird, right? if so, what's the package that you have to install, is it just 'ia32'? 
i want to put it into the [help section]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Help_section") for 64bit users.

---

### Post by luder on 2007-04-29
Ok, I didn't had the ia32 libs installed, Thunderbird starts ok now. Thanks! Stiil have to test if the sound is working well, though.

---

### Post by Tanker Bob on 2007-04-29
Please let me know about the sound and hyperlinks.  If they work with the ia32 libs installed, I'll give the new version another shot.  I wasted hours on this last weekend and am not inclined to duplicate that effort for nothing.

---

### Post by Tanker Bob on 2007-04-29
Well, I tried using the script again to install TB 2.0 on my 64-bit system.  Exactly the same errors as before--no sound, no hyperlinks, and the error console had the same errors.  I have the ia32 and lib32asound libs installed, but they didin't make any difference.  They were also installed the last time I tried, but one of the ia32 lib files didn't load before for some reason.  Reinstalling fixed that.

After deleting TB 2.0 and recovering back to 1.5.0.10, everything works fine again.  Somebody with more time than I have will have to figure this one out.  Backport Repository would be great.

---

### Post by FLCLFan on 2007-04-29
So umm... Is there a reason Thunderbird 2 (AMD64) is not in the repositories???

---

### Post by kwaanens on 2007-04-30
Can you read? Why not read the whole thread, or at least the first page of it? TB2 was too late for release. Packages need to be tested, you know.

Still hoping for a backport... 6 months of 1.5 is a long time... And 1.5 to 2.0 is a pretty long jump, feature wise.

- Ketil

---

### Post by luder on 2007-04-30
> **Tanker Bob said:**
> Please let me know about the sound and hyperlinks.

Sound doesn't work for me, either... Didn't test the hyperlinks.

---

### Post by Tanker Bob on 2007-04-30
> **luder said:**
> Sound doesn't work for me, either... Didn't test the hyperlinks.
I tried it again as well and neither worked for me after installing all the 32-bit libraries.  Looks like a bust in 64-bit Feisty until the Ubuntu folks add it to the respository.

---

### Post by hamil on 2007-04-30
Thanks for the script, it made the install of TB2 easy. I did run into some issues with the backup of the mail though, it refused to copy the cookies.txt file, which belongs to root.

After the install, I was not able to open any links from within TB, so i created the user.js as stated earlier in this post, and added this content to it:
[code]user_pref("network.protocol-handler.app.ftp","/usr/local/bin/Iceweasel32");
user_pref("network.protocol-handler.app.http","/usr/local/bin/Iceweasel32");
user_pref("network.protocol-handler.app.https","/usr/local/bin/Iceweasel32");[/usr]

But clicking the links in the mail, would not open the links in IceWeasel. Have tried to restart both apllications, restart X and even a reboot. Nothing happens ...

---

### Post by nanotube on 2007-04-30
> **hamil said:**
> Thanks for the script, it made the install of TB2 easy. I did run into some issues with the backup of the mail though, it refused to copy the cookies.txt file, which belongs to root.

After the install, I was not able to open any links from within TB, so i created the user.js as stated earlier in this post, and added this content to it:
```
user_pref("network.protocol-handler.app.ftp","/usr/local/bin/Iceweasel32");
user_pref("network.protocol-handler.app.http","/usr/local/bin/Iceweasel32");
user_pref("network.protocol-handler.app.https","/usr/local/bin/Iceweasel32");
```

But clicking the links in the mail, would not open the links in IceWeasel. Have tried to restart both apllications, restart X and even a reboot. Nothing happens ...

well, from the [gentoo wiki]("http://gentoo-wiki.com/TIP_Integrate_Thunderbird_and_Firefox"), the following advice:
# check your typing
# make sure the path to Firefox is correct (with "which firefox" for example)
# double check your typing 

are you sure about the capitalization of Iceweasel32, and the path? what's your output for 
```
which Iceweasel32
```

another thing to check is if after a restart, thunderbird actually reads these preferences. in thunderbird go to edit>preferences>advanced>config editor, and put in "handler.app" in the filter. these pref settings should show up. if not, then you have either 
# put user.js in incorrect location (should be in ~/thunderbird/blabla.default), 
# mistyped the filename (should be "user.js"), 
# or gave user.js incorrect permissions (should be owned by your user, and have at least u+r on it).

---

### Post by hamil on 2007-04-30
> **nanotube said:**
> well, from the [gentoo wiki]("http://gentoo-wiki.com/TIP_Integrate_Thunderbird_and_Firefox"), the following advice:
# check your typing
# make sure the path to Firefox is correct (with "which firefox" for example)
# double check your typing 

are you sure about the capitalization of Iceweasel32, and the path? what's your output for 
```
which Iceweasel32
```

another thing to check is if after a restart, thunderbird actually reads these preferences. in thunderbird go to edit>preferences>advanced>config editor, and put in "handler.app" in the filter. these pref settings should show up. if not, then you have either 
# put user.js in incorrect location (should be in ~/thunderbird/blabla.default), 
# mistyped the filename (should be "user.js"), 
# or gave user.js incorrect permissions (should be owned by your user, and have at least u+r on it).

Well, I am sure that Iceweasel is with capital I, the which gave the output I expected (I checked this before I created the user file):
/usr/local/bin/Iceweasel32

From Thunderbird, I can see the correct path for Iceweasel showing up for ftp, http and https.

The user file has these rights:
-rw-r--r-- 1 lars lars 231 2007-04-30 17:21 /home/lars/.mozilla-thunderbird/3gpdz1g8.default/user.js
Where lars is the normal user

---

### Post by nanotube on 2007-05-01
> **hamil said:**
> Well, I am sure that Iceweasel is with capital I, the which gave the output I expected (I checked this before I created the user file):
/usr/local/bin/Iceweasel32

From Thunderbird, I can see the correct path for Iceweasel showing up for ftp, http and https.

The user file has these rights:
-rw-r--r-- 1 lars lars 231 2007-04-30 17:21 /home/lars/.mozilla-thunderbird/3gpdz1g8.default/user.js
Where lars is the normal user

in that case, i'm stumped. :|

---

### Post by hamil on 2007-05-01
Well, I am too.. :) 

Will have to live with copy link, and then paste it into the browser for now ...

---

### Post by happysmileman on 2007-05-01
I used the script and links work, but sound doesn't...

---

### Post by nanotube on 2007-05-01
> **hamil said:**
> Well, I am too.. :) 

Will have to live with copy link, and then paste it into the browser for now ...

hmm, so what happens when you actually click on a link? nothing at all?

also, what do you have set in your system>preferences>preferred applications ? maybe setting that to iceweasel will work...?

---

### Post by nanotube on 2007-05-01
for sound in thunderbird, this is not really a "fix", but a workaround: you can try the mailbox alert extension:
[https://addons.mozilla.org/en-US/thunderbird/addon/2610](https://addons.mozilla.org/en-US/thunderbird/addon/2610)

---

### Post by Tanker Bob on 2007-05-01
Thanks for pointing out the extension, nanotube.  But, why do we need workarounds?  Is there something so compelling about TB 2.0 that we can't live without it until all this is sorted out?  64-bit 1.5.0.10 works fine for me without all the workarounds and hastle that 32-bit 2.0 requires.

---

### Post by kwaanens on 2007-05-01
> **Tanker Bob said:**
> Is there something so compelling about TB 2.0 that we can't live without it until all this is sorted out?  64-bit 1.5.0.10 works fine for me without all the workarounds and hastle that 32-bit 2.0 requires.

<disclaimer>
Not really directed towards you, Tanker Bob. I have just been building up to make this kind of statement, and your wording (or maybe, my associations to your wording) gave me an excuse.
</disclaimer>

You see, these kinds of comments are starting to bug me a little.

Why, oh, why, can't people "satisfied with the current version" stop posting in "I wish there was an update available now"-threads. This currently applies to at least Thunderbird and Pidgin threads around here.

If you're happy with current version, good for you! But respect that others have a wish/ need/ whatever for the latest version of the same apps.

Users making requests for more updated stuff, gets told to pipe down, and stop demanding stuff. (See for instance [this]("http://ubuntuforums.org/showthread.php?p=2568599") thread.) Well, why should I continue using an OS where you won't get updated apps (that are installed in an easy fashion, that is easy to administer, i.e. no make && make install, and the like), and on top, you get trampled down for even bringing some criticism on this subject to the table.

-- Ketil

---

### Post by nanotube on 2007-05-01
> **Tanker Bob said:**
> Thanks for pointing out the extension, nanotube.  But, why do we need workarounds?  Is there something so compelling about TB 2.0 that we can't live without it until all this is sorted out?  64-bit 1.5.0.10 works fine for me without all the workarounds and hastle that 32-bit 2.0 requires.

well, if you are happy with 1.5 then there's no hurry to upgrade. but you went to this thread looking for tb2, so you wanted it for /some/ reason eh? :)
a brief rundown of the new features in tb2 is here:
[http://www.mozilla.com/en-US/thunderbird/features.html](http://www.mozilla.com/en-US/thunderbird/features.html)

in my opinion, the most useful of those are improved search, custom tags (a la gmail), and new mail notifications.

and, it also seems to be quite a bit more responsive than tb1.5, but that could be just my subjective opinion. :)

---

### Post by Tanker Bob on 2007-05-01
> **kwaanens said:**
> <disclaimer>
Not really directed towards you, Tanker Bob. I have just been building up to make this kind of statement, and your wording (or maybe, my associations to your wording) gave me an excuse.
</disclaimer>

You see, these kinds of comments are starting to bug me a little.

Why, oh, why, can't people "satisfied with the current version" stop posting in "I wish there was an update available now"-threads. This currently applies to at least Thunderbird and Pidgin threads around here.

If you're happy with current version, good for you! But respect that others have a wish/ need/ whatever for the latest version of the same apps.

Users making requests for more updated stuff, gets told to pipe down, and stop demanding stuff. (See for instance [this]("http://ubuntuforums.org/showthread.php?p=2568599") thread.) Well, why should I continue using an OS where you won't get updated apps (that are installed in an easy fashion, that is easy to administer, i.e. no make && make install, and the like), and on top, you get trampled down for even bringing some criticism on this subject to the table.

-- Ketil 
Ketil,

No offense taken.  If you read back to the beginning of this thread, you will see that I was very interested in using TB 2.0.  I've spent hours trying to get it to run properly on 64-bit Kubuntu Feisty.  However, since many of us have been unsuccessful in getting some basic functionality like sound and hyperlinks to work properly, I have to retreat to 1.5.0.10.  Others seem to find it acceptable to employ work-arounds that diminish TB's ease of use.  I was just legitimately curious as to why others thought such measures worthwhile.  It was an honest question, not an indictment of progress.

---

### Post by fearpi on 2007-05-01
When running the script at

[http://pykeylogger.sourceforge.net/installnewthunderbird.sh](http://pykeylogger.sourceforge.net/installnewthunderbird.sh)

I get the following error:

trap: 18: ERR: bad trap

Anyone know why?

---

### Post by nanotube on 2007-05-01
> **fearpi said:**
> When running the script at

[http://pykeylogger.sourceforge.net/installnewthunderbird.sh](http://pykeylogger.sourceforge.net/installnewthunderbird.sh)

I get the following error:

trap: 18: ERR: bad trap

Anyone know why?

the scripts have a support forum here: [http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251) , you really should have posted there
lucky i happen to be monitoring this thread as well. ;)
anyway, nobody has reported something like this before. when exactly does it occur (post the complete output that you get from running the script). 
you'd do better to start a new thread with your issue in [our support forum]("http://ubuntuforums.org/forumdisplay.php?f=251"), that way maybe aysiu will help, too.

---

### Post by fearpi on 2007-05-01
What I posted is the entirety of the output. But thanks, I will post in the other forum.

---

### Post by nanotube on 2007-05-01
> **fearpi said:**
> What I posted is the entirety of the output. But thanks, I will post in the other forum.

hmm...  what is the exact commandline that you use to run the script? 
what is your output of 
```
bash --version
```
what is your output of
```
grep -C3 "errexit" installnewthunderbird.sh
```
(adjust the path to point to the location of the script)

---

### Post by fearpi on 2007-05-01
```
$ bash --version
GNU bash, version 3.2.13(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.

```

```
$ grep -C3 "errexit" installnewthunderbird.sh
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

VERSION="3.1.0"

```

---

### Post by nanotube on 2007-05-01
that looks ok. what about the commandline you use?

---

### Post by kjano on 2007-05-04
for me the following works very easy:

download [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/) thunderbird2 and unzip it.
copy the content (!) of the folder to your home into ./mozilla-thunderbird.

open a shell and change to the mozilla-thunderbird directory. then type in ./thunderbird (not as root!). now you can leave thunderbird again and run it with ./thunderbird -ProfileManager . now create a new profile and just chose your old profile folder under "change folder".

thats all :-)

---

### Post by Tanker Bob on 2007-05-04
> **kjano said:**
> for me the following works very easy:

download [http://www.mozilla.com/en-US/thunderbird/](http://www.mozilla.com/en-US/thunderbird/) thunderbird2 and unzip it.
copy the content (!) of the folder to your home into ./mozilla-thunderbird.

open a shell and change to the mozilla-thunderbird directory. then type in ./thunderbird (not as root!). now you can leave thunderbird again and run it with ./thunderbird -ProfileManager . now create a new profile and just chose your old profile folder under "change folder".

thats all :-)
That only works if you are running 32-bit Feisty.  TB 2.0 doesn't work right in 64-bit Feisty.

---

### Post by MadMan2k on 2007-05-05
heres a straight backport from gutsy to feisty:
[http://uploader.polorix.net//files/140/thunderbird.tar](http://uploader.polorix.net//files/140/thunderbird.tar)

---

### Post by Tanker Bob on 2007-05-05
> **MadMan2k said:**
> heres a straight backport from gutsy to feisty:
[http://uploader.polorix.net//files/140/thunderbird.tar](http://uploader.polorix.net//files/140/thunderbird.tar)
That looks like a 32-bit package.  Is that correct?

---

### Post by MadMan2k on 2007-05-05
yes

---

### Post by Tanker Bob on 2007-05-05
Is there a 64-bit package over there at Gutsy?

---

### Post by jonny_boy27 on 2007-05-06
I get an unexpected end of file error with that gutsy tarball :S

---

### Post by profjohn on 2007-05-06
I've compiled the packages from the gutsy repos for feisty using pbuilder. They work for me, enjoy.
[thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874170/thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb]("http://rapidshare.com/files/29874429/thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb")
[thunderbird_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874483/thunderbird_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874536/thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb")

You'll have to uninstall Thunderbird 1.5 first for it to work, something like
> sudo apt-get remove mozilla-thunderbird

This is because thunderbird has changed in gutsy to just 'thunderbird' as opposed to 'mozilla-thunderbird'. I'm guessing mozilla-thunderbird will become a metapackage in gutsy just like mozilla-firefox did.

---

### Post by Tanker Bob on 2007-05-06
> **profjohn said:**
> I've compiled the packages from the gutsy repos for feisty using pbuilder. They work for me, enjoy.
[thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874170/thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb]("http://rapidshare.com/files/29874429/thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb")
[thunderbird_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874483/thunderbird_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874536/thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb")
Thanks, profjohn.  The thunderbird_2.0.0.0-0ubuntu3_amd64.deb install worked!  I now get sound and hyperlinks in messages work.  

I ran into a few problems, though.  First I had to uninstall TB 1.5.0.10, otherwise the new version refused to install.  After I did that, there was one missing dependency on TB 2.0 install--libnspr4-0d.  Thunderbird would not configure without it.  I installed that library from KPackage after the TB 2.0 install, and it installed fine, and then the TB 2.0 configuration completed automatically as well.

Thank you so much for taking the time and effort to put these files together! :guitar:

EDIT: I found two dead symbolic links that were installed in /usr/lib/thunderbird/.  They were 'libnssckbi.so' which pointed to a non-existent /nss/ directory somewhere and 'searchjplugins' that pointed to a like name in the firefox directory.  I found several libnssckbi.so files in the system, and linked TB 2.0 to the one in the /usr/lib/firefox directory assuming that a fellow mozilla app wouldn't steer me wrong.  There's no searchjplugins anywhere in the system.  Don't know if any of this matters, but TB 2.0 seems to work OK in normal use.

---

### Post by AppleCrow on 2007-05-10
You can get thunderbird 2.0.0 for feisty here, with the locale languages :
deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main

Dependencies have been modded to match feisty one (nss3 and nspr4 aren't needed as we use firefox nss)

---

### Post by Tanker Bob on 2007-05-10
> **AppleCrow said:**
> You can get thunderbird 2.0.0 for feisty here, with the locale languages :
deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main

Dependencies have been modded to match feisty one (nss3 and nspr4 aren't needed as we use firefox nss)
Thanks.  There are just the i386 packages, though.

---

### Post by tuga on 2007-05-10
Thank You profjohn.
I was having problems to open the email attachments. After install your deb package the attachments are opening fine.

---

### Post by geco on 2007-05-12
I am an Edgy user... any idea if Tdb2 will be available for Edgy too? :confused:

edit:
I upgraded to Feisty ;)

---

### Post by profjohn on 2007-05-12
> **geco said:**
> I am an Edgy user... any idea if Tdb2 will be available for Edgy too? :confused:
I had a go backporting from Gutsy to Edgy using prevu but the build fails on something called libxpconnect.so

---

### Post by joshuacollins on 2007-05-21
i am also having the 'bad trap' error on the sh file...  here's my output that another poster requested:

> #######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

echo "This is no longer a maintained version of the script. Get the latest version at

(it cuts off there)...

any ideas?
:(

---

### Post by nanotube on 2007-05-21
> **joshuacollins said:**
> i am also having the 'bad trap' error on the sh file...  here's my output that another poster requested:


(it cuts off there)...

any ideas?
:(

hi
i never got to the root of that problem, since the original poster never came back to help me troubleshoot...
but, head over here [http://ubuntuforums.org/showthread.php?t=450621](http://ubuntuforums.org/showthread.php?t=450621)
and try out the new version of the install scripts. please report back if you have any problems.

---

### Post by gnomefreak on 2007-05-25
At this moment we(ubuntu-mozillateam) are talking about backporting Tbird to feisty once the 1.5 mozilla branch is at EOS. Right now i we have a repo that you can find Tbird2.0 Ffox3.0 Ffox 2.0.0.3 (the one that will be in gutsy with the exception that is it not built using libhunspell-dev 1.1.5-6 since when we did build it on that OO.o and others broke, howhere it uses the new builds of libnss and libnspr (they are now built seperate. Repo also has Iceape1.1.1 that will be in gutsy. The repos can be found at 

[https://wiki.ubuntu.com/MozillaTeam/PreviewArchives](https://wiki.ubuntu.com/MozillaTeam/PreviewArchives)

That link explains how to file bugs on the packages in those repos.

---

### Post by Sodki on 2007-06-04
I know that PPC is an unsupported platform, but is there any chance that you could provide PPC binaries OR instructions on how to compile our own "backported version"? I've used Gentoo for a few years now and I'm not afraid of compiling stuff. I just want to learn how to do it/integrate it the proper way with Ubuntu's package manager. Thank you.

---

### Post by gnomefreak on 2007-06-04
I will ask someone with a ppc to spin it but should be fairly simple. I cant promise it will work and not faile but you can try the same thing that we do with 386 and 64 bit. make a dir in home for the build than cd into it. next with my repo enabled run apt-get source thunderbird. next cd into the source dir than simple enough install all depends on it (sudo apt-get build-dep thunderbird. than once you have everything installed for it in the same dir run dpkg-buildpackage -rfakeroot -kYOURKEYID  

you can leave off -kKEYID if you like all it does it sign the .dsc file. if all goes well you will have source and binaries for thunderbird now just cd .. and dpkg -i packagename.deb

the packages you will need off top of my head to build this are fakeroot bzip2, debhelper (>= 5), quilt, patchutils (>= 0.2.25), cdbs (>= 0.4.27-1), libx11-dev, libxt-dev, libgtk2.0-dev (>= 2.8), zlib1g-dev, liborbit2-dev, libidl-dev (>= 0.8.0), zip, libxft-dev, libfreetype6-dev, libpng12-dev, libjpeg62-dev, libxrender-dev, libxinerama-dev, libcairo2-dev, libgnome2-dev, libgconf2-dev, libgnomevfs2-dev, libgnomeui-dev, sharutils, m4, binutils (>= 2.17-1) [mips mipsel], libhunspell-dev, libnss3-dev, libnspr4-dev, docbook-to-man

if some of these packages are not the same as the ones in ppc than you can try ppc versions but ive never built tbird on ppc. but taht should be it. 

Please let me know if you run into any issues with it and i will see what i can come up with on it. sonn i will be posting more info on the repos and hopefully i will have a ppc or someone with a ppc to build the packages for me so i can add ppc repo.

---

### Post by DougieFresh4U on 2007-06-07
Using T.B.2, it freezes on start up. New mail loads then freezes. I can only force quit. If I wait for some thing to happen, it crashes and disappears.
When I re-start after force quit, new mail is there and all is fine

---

### Post by gnomefreak on 2007-06-08
What version of tbird2.0 are you using and how did you install it? example: compile it yourself, my repo, download extract and ./thunderbird? What version of ubuntu and what arch is it? Do you have or can you get a backtrace of the freeze.

---

### Post by DougieFresh4U on 2007-06-08
**[QUOTE=gnomefreak;2804473]What version of tbird2.0 are you using and how did you install it? example: compile it yourself, my repo, download extract and ./thunderbird? What version of ubuntu and what arch is it? Do you have or can you get a backtrace of the freeze.[/QUOTE**

Thank you so much for your response :)]

I installed via Add/Remove.
I am using T.B. on my Feisty machine i386. I am not sure how to do a back trace and what log  would I find errors in?

---

### Post by gnomefreak on 2007-06-08
ok lets start with running apt-cache policy thunderbird if that doesnt give you anything try apt-cache mozilla-thunderbird.

Try going to [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) and under the crashes title run those steps just replace firefox named packages with thunderbird. you may need to use pittis repo to get -dbgsym packages instead of dbg for thunderbird since we dont build -dbg with tbird (may be changing in near future)
pittis repo can be found at:
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)
once you add the repo than go to the mozilla page i gave you above and install the -dbgsym packages if you cant find -dbg packages. I need to get working on the wiki so i dont have to give different links, but for now that is pretty much how you would go about it.

---

### Post by DougieFresh4U on 2007-06-08
> **gnomefreak said:**
> ok lets start with running apt-cache policy thunderbird if that doesnt give you anything try apt-cache mozilla-thunderbird.

Try going to [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) and under the crashes title run those steps just replace firefox named packages with thunderbird. you may need to use pittis repo to get -dbgsym packages instead of dbg for thunderbird since we dont build -dbg with tbird (may be changing in near future)
pittis repo can be found at:
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)
once you add the repo than go to the mozilla page i gave you above and install the -dbgsym packages if you cant find -dbg packages. I need to get working on the wiki so i dont have to give different links, but for now that is pretty much how you would go about it.

Thanks, working on it.
I will post the outcome, again thanks

Dougie

---

### Post by Sodki on 2007-06-08
> **gnomefreak said:**
> I will ask someone with a ppc to spin it but should be fairly simple. I cant promise it will work and not faile but you can try the same thing that we do with 386 and 64 bit. make a dir in home for the build than cd into it. next with my repo enabled run apt-get source thunderbird. next cd into the source dir than simple enough install all depends on it (sudo apt-get build-dep thunderbird. than once you have everything installed for it in the same dir run dpkg-buildpackage -rfakeroot -kYOURKEYID
Thank you for your thorough answer, I learned a lot from it. There seems to be an error with libfreetype6-dev depending on an older version of libfreetype, but I managed to work my way around it.

Unfortunately, theres a bigger problem. the installation of libnspr4-dev requires the removal of many packages:

The following extra packages will be installed:
  libnspr4-0d
The following packages will be REMOVED:
  alacarte bug-buddy contact-lookup-applet deskbar-applet ekiga epiphany-browser epiphany-extensions evolution
  evolution-data-server evolution-exchange evolution-plugins firefox firefox-gnome-support gaim gcjwebplugin-4.1
  gnome-applets gnome-control-center gnome-panel gnome-session gnome-terminal gnome-user-guide libcamel1.2-10
  libebook1.2-9 libedata-book1.2-2 libedataserverui1.2-8 libnspr4 libnss3 liferea liferea-mozilla nautilus
  nautilus-cd-burner nautilus-sendto ubuntu-desktop ubuntu-docs yelp
The following NEW packages will be installed:
  libnspr4-0d libnspr4-dev

---

### Post by gnomefreak on 2007-06-09
this is known and was fixed in gutsy. since we changed the way nss and nspr were built in gutsy we are unable to change this for feisty. I cant remember if this even happened on feisty. but make sure if you are on gutsy to update everything. I also suggest you building it in a chroot not on your main system sue to  other things that can happen. 
To set up a chroot please follow instructions at:
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

The best way to get a hold of me or asac is on irc.freenode.net channel #ubuntu-mozillateam. We are the 2 people mainly package mozilla apps for ubuntu. Monday-friday are the best days.

---

### Post by dysonsphere23 on 2007-06-12
> **AppleCrow said:**
> You can get thunderbird 2.0.0 for feisty here, with the locale languages :
deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main

Dependencies have been modded to match feisty one (nss3 and nspr4 aren't needed as we use firefox nss)

Thanks for this.  I think it wants me to uninstall 1.5 first, though.  I have no problem with doing that but I want to make sure that this will not wipe out all my saved mail and address book and account preferences etc.  Any advice on how to keep all that stuff in the transition?

---

### Post by gnomefreak on 2007-06-12
I cant answer for apples package but no it shouldnt touch your existing profile

---

### Post by nanotube on 2007-06-12
> **dysonsphere23 said:**
> Thanks for this.  I think it wants me to uninstall 1.5 first, though.  I have no problem with doing that but I want to make sure that this will not wipe out all my saved mail and address book and account preferences etc.  Any advice on how to keep all that stuff in the transition?

well, it shouldn't touch your actual data, but just in case, you may want to back up your ~/.mozilla directory. that's the default location of your firefox profile.

---

### Post by UI-Freak on 2007-06-13
> **DougieFresh4U said:**
> Using T.B.2, it freezes on start up. New mail loads then freezes. I can only force quit. If I wait for some thing to happen, it crashes and disappears.
When I re-start after force quit, new mail is there and all is fine

I have this problem as well. Didn't compile or anything, I don't remember now where I got the installer for Thunderbird... Automatix?

**[COLOR=Red]SOLVED: Problem with Thunderbird 2.0.0 and third party themes. Use the default theme and it will probably work again. Did for me.[/COLOR]**

---

### Post by colo505 on 2007-06-19
> **profjohn said:**
> I've compiled the packages from the gutsy repos for feisty using pbuilder. They work for me, enjoy.
[thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874170/thunderbird-gnome-support_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb]("http://rapidshare.com/files/29874429/thunderbird-locale-en-gb_2.0.0.0_1-0ubuntu1_all.deb")
[thunderbird_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874483/thunderbird_2.0.0.0-0ubuntu3_amd64.deb")
[thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb]("http://rapidshare.com/files/29874536/thunderbird-dev_2.0.0.0-0ubuntu3_amd64.deb")

You'll have to uninstall Thunderbird 1.5 first for it to work, something like


This is because thunderbird has changed in gutsy to just 'thunderbird' as opposed to 'mozilla-thunderbird'. I'm guessing mozilla-thunderbird will become a metapackage in gutsy just like mozilla-firefox did.

Thanks! Any chance of getting the latest version debs?

---

### Post by BoogieKnight on 2007-08-02
this site has 32 and 64 bit .deb packages for Thunderbird 2.0.0.5

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

i had to install the thunderbird-locales package first in order to install the application package but after that everything runs perfect. hope this helps.

---

