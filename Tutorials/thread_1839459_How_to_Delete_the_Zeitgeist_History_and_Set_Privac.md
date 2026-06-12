---
title: "How to Delete the Zeitgeist History and Set Privacy Defaults"
date: 2011-09-05
forum: Tutorials
---

### Post by SilverWave on 2011-09-05
Is Zeitgeist logging too much information about you?

> "Zeitgeist is a service which logs the user&#8217;s activities and events  (files opened, websites visits, conversations held with other people,  etc.) and makes relevant information available to other applications. It  is able to establish relationships between items based on similarity  and usage patterns." See **[here]("https://launchpad.net/ubuntu/+source/zeitgeist")**. ________________________________________

Here is my current easy fix for this issue:

**"Plan A"**  :-)

Uninstalling Zeitgeist can cause issues as it is used by Unity and  is expected to be available.
Removal could also be a problem in the future as  other programs may look for it being installed.
 Here is my simple solution:
 
[LIST=1]
[*]Remove the old databases and use the &#8220;&#8211;replace&#8221; argument to generate new files.
[*]Then change permissions so that Zeitgeist can&#8217;t read or write to them. :-)
[/LIST]
 ________________________________________

 # Delete previous logging.
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
``` [here.]("http://askubuntu.com/questions/34592/how-to-clear-recently-used-files")

 # Limit Zeitgeist Logging - cannot read or write.
```
chmod -rw ~/.local/share/zeitgeist/activity.sqlite*
``` [here.]("http://johanharjono.com/archives/836")

 Note: In place of the rm command I navigated to the folder and deleted everything manually.

Best of Luck. :-)

________________________________________

**Dash:**
Bear in mind that this will limit what the Dash can do... basically turning it in to an application menu.
Searching will not work.
That's not a problem for me as that&#8217;s exactly what I want.
Here is how I use it:
Dash> Media Apps
Dash> Internet Apps
Dash> More Apps > Filter result > Type

**Run A Command:**
Alt+F2 works fine.

**Searching:**
Searching for Files from Dash will not work.
Here are some alternatives:
File Manager > Search
Dash >More apps > Search for Files
Dash >More apps > Catfish
________________________________________

** If that is a little extreme for you, here is an alternative:**

"Plan B" using the  [activity-log-manager]("http://ubuntuforums.org/showpost.php?p=11238420&postcount=4").

---

### Post by _d_ on 2011-09-10
Cheers, I was actually wondering how to just completely get rid of Zeitgeist as it's not really my cup of tea and I don't like things like this tracking what I do, where I go, and who I talk to and everything I say to them. :P

+1

---

### Post by SilverWave on 2011-09-10
> **_d_ said:**
> Cheers, I was actually wondering how to just completely get rid of Zeitgeist as it's not really my cup of tea and I don't like things like this tracking what I do, where I go, and who I talk to and everything I say to them. :P

+1


Glad you liked it but I have updated with a better solution. 8)8)8)

I am going to keep the original on as plan B.

---

### Post by SilverWave on 2011-09-10
I am archiving the original solution here, as I have found an easier way, and I am going to be changing the landing page to reflect it.
__________________________________________________
 
Is Zeitgeist logging too much information about you?

If so below is an explanation of how to set some reasonable defaults on   what information is logged and which applications can use Zeitgeist   logging.

> "Zeitgeist is a service which logs the user&#8217;s activities and  events  (files opened, websites visits, conversations held with other  people,  etc.) and makes relevant information available to other  applications. It  is able to establish relationships between items based  on similarity  and usage patterns." See **[here]("https://launchpad.net/ubuntu/+source/zeitgeist")**. You will need to add a ppa (ppa:zeitgeist/ppa) to gain access to the required software (the activity-log-manager).

See the Zeitgeist PPA home page **[here]("https://launchpad.net/%7Ezeitgeist/+archive/ppa")**.

```
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update
sudo apt-get upgrade
zeitgeist-daemon --replace
sudo apt-get install activity-log-manager
```Note: [How do I use software from a PPA?]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

Once installed use the dash to run the activity-log-manager

From the manager dialogue you can stop all logging with the  button bottom right.

Note: This can cause issues with Dash... so you are better off clicking  the "Files tab" and ticking the things you don&#8217;t want logged.

Once you are finished you will need to clear the history of the items that were logged previously.

On the "History tab" set the dates and click delete.

Although I haven&#8217;t done this you can also blacklist applications from the "Applications tab".

Best of Luck. :smile:

---

### Post by SilverWave on 2011-09-10
> **SilverWave said:**
> Is Zeitgeist logging too much information about you?

________________________________________

Here is my current easy fix for this issue:

"Plan A"  :-)

Uninstalling Zeitgeist can cause issues as it is used by Unity and  is expected to be available.
Removal could also be a problem in the future as  other programs may look for it being installed.
 Here is my simple solution:
 
[LIST=1]
[*]Remove the old databases and use the &#8220;&#8211;replace&#8221; argument to generate new files.
[*]Then change permissions so that Zeitgeist can&#8217;t read or write to them. :-)
[/LIST]
  


**Dash:**
Bear in mind that this will limit what the Dash can do... basically turning it in to a application finder/launcher.
That's not a problem for me as that&#8217;s exactly what I want.

**Run A Command:**
Alt+F2 works fine as well.

**Searching:**
Searching for Files from Dash does not work.
Here are some alternatives:
File manager > Search
Dash >More apps > Search for Files
Dash >More apps > Catfish

---

### Post by reset042 on 2012-02-12
Firstly, thank you, Silverwave, for your post.

I cannot express in a public forum how much I loathe crap like Zeitgeist. One of the reasons that I looked at Linux and Ubuntu in the first place was because of crap like this from Microsoft. And now Ubuntu has created something even worse! If my office were to be burgled, I do not want the evil gits getting any business information - including my clients' information - from my computer whatsoever. So I do not want Zeitgeist or anything like it. I use Truecrypt.

It's a real pain because now I've started looking at alternatives to Ubuntu, when there are so many other things I love about Ubuntu. (I know I can ditch Unity, but if I'm going to do that I might as well get completely away from Ubuntu in case any more crap like this comes up in future...) 

I could go on but I'd better end this rant now and get to the point of this reply!:

I followed your instructions in Plan A, but when I ran zeitgeist-daemon --replace I saw this output:
```
WARNING **: recent-manager-provider.vala:125: Desktop file for firefox-bin was not found
DEBUG: zeitgeist-datahub.vala:174: Inserting 300 events
```What the--!? *Inserting*? What is this Zeitgeist thing ***doing***? Sure enough, instead of seeing, as I'd hoped, a blank recent files lens, there were just a load of different files.

A while back I tried uninstalling Zeitgeist completely but my system seemed to become unstable, so I re-installed it and the Activity Log Manager set to stop logging, but it still seems to be doing bad things. For me this is another reason why crap like this should not be integrated so tightly into Ubuntu. Security weaknesses like Zeitgeist should be an option, not forced onto users.

Thanks again.

---

### Post by SilverWave on 2012-02-12
> **reset042 said:**
> Firstly, thank you, Silverwave, for your post.

I cannot express in a public forum how much I loathe crap like Zeitgeist. One of the reasons that I looked at Linux and Ubuntu in the first place was because of crap like this from Microsoft. And now Ubuntu has created something even worse! If my office were to be burgled, I do not want the evil gits getting any business information - including my clients' information - from my computer whatsoever. So I do not want Zeitgeist or anything like it. I use Truecrypt.

It's a real pain because now I've started looking at alternatives to Ubuntu, when there are so many other things I love about Ubuntu. (I know I can ditch Unity, but if I'm going to do that I might as well get completely away from Ubuntu in case any more crap like this comes up in future...) 

I could go on but I'd better end this rant now and get to the point of this reply!:

I followed your instructions in Plan A, but when I ran zeitgeist-daemon --replace I saw this output:
```
WARNING **: recent-manager-provider.vala:125: Desktop file for firefox-bin was not found
DEBUG: zeitgeist-datahub.vala:174: Inserting 300 events
```What the--!? *Inserting*? What is this Zeitgeist thing ***doing***? Sure enough, instead of seeing, as I'd hoped, a blank recent files lens, there were just a load of different files.

A while back I tried uninstalling Zeitgeist completely but my system seemed to become unstable, so I re-installed it and the Activity Log Manager set to stop logging, but it still seems to be doing bad things. For me this is another reason why crap like this should not be integrated so tightly into Ubuntu. Security weaknesses like Zeitgeist should be an option, not forced onto users.

Thanks again.

Hi reset042,

Hopefully 12.04 will fix all this but in the meantime the key IIRC is to delete activity.sqlite then make it read only before anything gets a chance to write to it...

my permissions are -r-r-r- and the date is 04/09/11 53.0KB, (see the screen shot).

---

### Post by SilverWave on 2012-02-12
> **reset042 said:**
> Firstly, thank you, Silverwave, for your post.

...


Oh and I use ClasicMenu Indicator in place of Dash.

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)

[IMG]http://www.florian-diesch.de/_images/classicmenu-indicator.png[/IMG]

---

### Post by reset042 on 2012-02-14
> **SilverWave said:**
> Hopefully 12.04 will fix all this but in the meantime the key IIRC is to delete activity.sqlite then make it read only before anything gets a chance to write to it...

Thanks again SilverWave! I'm not holding my breath about 12.04 fixing this. Indeed, if what I read about new application menus (that seem to be based on an idea Microsoft ditched years ago...) and other stuff that's going to be in 12.04, then I shan't install it. Want a laugh? At one point I thought about installing Ubuntu 10.10 next!

It still irks me that Zeitgeist saw fit to add 300 items which, presumably, it must have got from GTK?

> Oh and I use ClasicMenu Indicator in place of Dash.
[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)A huge thank you for that link! Why did I not know about this earlier? That is perfect! A sane menu system in Unity! 

Want another laugh? After installation, the first app that showed in the ClassicMenu under accessories at the top was Zeitgeist's very own Activity Log Manager, so to test that the ClassicMenu was working I clicked and launched Activity Log Manager. I don't know what possessed me, but as Activity Log Manager was open - even though logging is stopped, apparently - I then clicked the 'Forget my activities... Delete' button. BAM! Instant black screen of death, followed by the Ubuntu login screen. 20 minutes' work lost. 

I am more and more convinced that the all too frequent and random crashes my system is suffering are as a result of this tight integration of Zeitgeist into Unity and Ubuntu. 

So I now have another question: now that I have a sane and sensible menu system, do I need Zeitgeist at all? Can't I just get rid of it forever? I'm really strongly hoping for a yes answer to that...

Thanks again, SilverWave

---

### Post by SilverWave on 2012-02-14
> **reset042 said:**
> Thanks again SilverWave! I'm not holding my breath about 12.04 fixing this. Indeed, if what I read about new application menus (that seem to be based on an idea Microsoft ditched years ago...) and other stuff that's going to be in 12.04, then I shan't install it. Want a laugh? At one point I thought about installing Ubuntu 10.10 next!

It still irks me that Zeitgeist saw fit to add 300 items which, presumably, it must have got from GTK?

A huge thank you for that link! Why did I not know about this earlier? That is perfect! A sane menu system in Unity! 

Want another laugh? After installation, the first app that showed in the ClassicMenu under accessories at the top was Zeitgeist's very own Activity Log Manager, so to test that the ClassicMenu was working I clicked and launched Activity Log Manager. I don't know what possessed me, but as Activity Log Manager was open - even though logging is stopped, apparently - I then clicked the 'Forget my activities... Delete' button. BAM! Instant black screen of death, followed by the Ubuntu login screen. 20 minutes' work lost. 


Hmm if you had made the file read only perhaps the crash out was because of this?  That is presumably the "'Forget my activities... Delete' button " must access the log to delete parts of it?

> 
I am more and more convinced that the all too frequent and random crashes my system is suffering are as a result of this tight integration of Zeitgeist into Unity and Ubuntu. 

So I now have another question: now that I have a sane and sensible menu system, do I need Zeitgeist at all? Can't I just get rid of it forever? I'm really strongly hoping for a yes answer to that...

Thanks again, SilverWave

I thought of the same thing but chose to just neuter it in place of removal, I was concerned that other parts of the OS would anticipate Zeitgeist being in place. YMMV :-)

---

### Post by chickenPie4breakfast on 2012-02-22
Just to say I like Zeitgeist and love the way programs like Kupfer (a launcher) can use it so that I can easily get to files I have used recently etc. I am glad it's included with Ubuntu

---

### Post by SilverWave on 2012-02-22
> **chickenPie4breakfast said:**
> Just to say I like Zeitgeist and love the way programs like Kupfer (a launcher) can use it so that I can easily get to files I have used recently etc. I am glad it's included with Ubuntu


Well "each to their own" but I still think Zeitgeist kills kittens ;-)

---

### Post by Whoopie on 2012-02-24
There's a package called activity-log-manager-control-center in Ubuntu 12.04. If you install this package, you can disable zeitgeist in the system settings under "Privacy".

---

### Post by SilverWave on 2012-02-24
> **Whoopie said:**
> There's a package called activity-log-manager-control-center in Ubuntu 12.04. If you install this package, you can disable zeitgeist in the system settings under "Privacy".


Great news :-)

Thanks.

---

### Post by SilverWave on 2012-03-03
> **Whoopie said:**
> There's a package called activity-log-manager-control-center in Ubuntu 12.04. If you install this package, you can disable zeitgeist in the system settings under "Privacy".

Just installed 12.04 and installed as you advised.

Hmm Turning Record Activity from On to Off seems to work but if you reopen it, it's still showing as On.

[EDIT] Looks as if my previous fix (changing permissions to activity.sqlite to -r-r-r-) is still in place even after the upgrade to 12.04.

Sweet :-)

---

### Post by hawthornso23 on 2012-05-16
I conjecture that Zeitgeist stores its on/off state in the database you have marked read only.

---

