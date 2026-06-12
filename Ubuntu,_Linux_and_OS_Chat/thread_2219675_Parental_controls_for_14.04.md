---
title: "Parental controls for 14.04"
date: 2014-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by mjasnik on 2014-04-25
Hi!

Short intro: my kid has his own computer running ArchLinux (awesome distro), as I'm responsible  parent I was limiting time for his account because be it good or bad  but one thing is clear that without control they spend too much time at  computer desk. I was using Timekpr to limit their time, Timekpr was  simple and functional and was really easy to set up as well. One day it  stopped working in ArchLinux, so I fixed it and all was fine to the day  when my son wanted to try Ubuntu, with all pre-checks made  it was one missing thing - parental controls. I didn't find any to be  working in Ubuntu, except for manual tinkering.

So as I liked  Timekpr I tried to find out what the problem is. Some time later it was  functional and working. I wrote new appindicator for it and fixed all  the things to be able to run it on Ubuntu 14.04. Indicator works in a  bit different fashion opposed to standard Timekpr client, I find it more  informative. My use case which I worked on is time limit for a day, say  2hrs computing at any time. Other methods were not tested carefully  and some combinations not at all. **So I want more user feedback!**

[B]Note:  this is by no means new Timekpr, all credits for Timekpr goes to  respective authors, except for my contribution to adapt it to latest Ubuntu and new appindicator for it!
[/B]
So here it is for You to try out:  [https://launchpad.net/~mjasnik/+archive/ppa](https://launchpad.net/~mjasnik/+archive/ppa) , add my PPA to the system  and install Timekpr. Post Your ideas and bugs here or create them on  lauchpad.
Instructions:
```
sudo apt-add-repository ppa:mjasnik/ppa
sudo apt-get update
sudo apt-get install timekpr
```

Then log out/in and see the changes.

I  have tested it only on 14.04 and it works, if it works on  other versions - good, if not - not sure, but maybe I'll fix it :) At  this stage please consider it as first beta :) When it will be good  enough I'll try to contact Timekpr maintainers and merge changes in their ppa,  although the project seems to be dead - I'll still try.
*Note: As this is parental controls users themselves will have no options for appindicator.*

Happy testing.

regards
Eduards

---

### Post by grumblebum2 on 2014-04-25
Hi mjasnik,
Nice job, see a few requests for simple time access controls like this. 
Tested in a couple of accounts and both the access duration and time frame worked and was duly logged out.
Seems to be working fine.

---

### Post by mjasnik on 2014-04-29
Hi grumblebum2,

thanks for testing, hope indicator is informative and works as intended. My son is main tester now, he says it's fine :)

regards
Mjasnik[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1910493")

---

### Post by mailhyoon on 2014-05-06
Can't wait until I try it (on my son) that is.
I have been using nanny - but would like to upgrade to 14.04 from 10.04, as this is much faster than 12.04 & great for older computers (precisely what we give to kids) with now matured Lubuntu.
Well, just wanted express my thanks & possibly suggest an improvement.
[LIST]
[*]One thing I always would like to have on the nanny was ability to add time for good behavior. Remotely would be great, but on screen is just fine. Just keep a teamviewer handy is all this requires to do this remotely.
[/LIST]
Still a great app! Keeping my son away from windows means less games & more mature behavior.:P

---

### Post by CaptainMark on 2014-05-07
I know its the sort of thing that isn't easy to add to an app like this but here goes anyway, I would like to see a true parental control app that rolls up a timekpr type time control and content filtering all into one easy to use program with a nice simple clean gui for parents who don't feel comfortable using the more complex tools like privoxy, dans guardian, iptables etc etc. 

It's been on my list of things to start working on for years but unfortunately I don't get much time for coding anymore.

---

### Post by dragonfly41 on 2014-05-07
This is a good addition to parental time control tools ..

Free version ...
[http://www.opendns.com/home-internet-security/parental-controls/opendns-home/](http://www.opendns.com/home-internet-security/parental-controls/opendns-home/)

Paying version ...
[http://www.opendns.com/home-internet-security/parental-controls/opendns-home-vip/](http://www.opendns.com/home-internet-security/parental-controls/opendns-home-vip/)

And quite easy to setup.

---

### Post by mjasnik on 2014-05-07
> **mailhyoon said:**
> Can't wait until I try it (on my son) that is.
Well, just wanted express my thanks & possibly suggest an improvement.
[LIST]
[*]One thing I always would like to have on the nanny was ability to add time for good behavior. Remotely would be great, but on screen is just fine. Just keep a teamviewer handy is all this requires to do this remotely. 
[/LIST]


**Existing functionality**
There is actually an on screen app to do that "Timekpr Control Panel" it was already there from original project and it has button "Add time Reward / Penalty". Details here: [http://www.omgubuntu.co.uk/2014/05/timekpr-restrict-computer-access-ubuntu](http://www.omgubuntu.co.uk/2014/05/timekpr-restrict-computer-access-ubuntu)
One thing that I did not understood is why they needed to run it as a root from terminal as it's perfectly working from Dash, just press <Super> and write "timekpr", choose "Timekpr Control Panel" and You'll get what You want, internally it uses "gksu" to authenticate and I verified it works on my sons computer.

**Remote admin thing**
I actually do add time remotely as well: my setup is 1h every day, that's what I configure in GUI app, but sometimes I just add more time for kids just as a reward, so to do that I need to connect to that box via ssh, find a file /var/lib/timekpr/<username which kids use>.time and add more time. Time there is measured in spent seconds, for instance if user was logged in for say, half an hour, then file will contain line 1800, if You need to add more time just subtract seconds from that time and you're good to go. Timekpr accepts negative numbers as well, if You would like to reward kids with additional hour (before they spend any of time) just change the line in that file to -3600. Not user friendly, I know :D and You need to learn math :D, but that's the way I do it for years in ArchLinux and now Ubuntu, additionally at the moment I do not have plan to implement any remote admin possibilities.

> **mailhyoon said:**
> 
Still a great app! Keeping my son away from windows means less games & more mature behavior.

Hey, that's until they learn what the wine is (not the drink of course) :)

---

### Post by mjasnik on 2014-05-07
> **CaptainMark said:**
> I know its the sort of thing that isn't easy to add to an app like this but here goes anyway, I would like to see a true parental control app that rolls up a timekpr type time control and content filtering all into one easy to use program with a nice simple clean gui for parents who don't feel comfortable using the more complex tools like privoxy, dans guardian, iptables etc etc. 

It's been on my list of things to start working on for years but unfortunately I don't get much time for coding anymore.

Yeah that might be very handy, BUT isn't this type of control for router/FW and not for standalone computer? Usually computers are hooked up to local net either wireless or wired, so there You set up whatever routing/FW rules You need for kids computer to restrict what sites they are allowed to visit, but when they take computer out of house that indicates they are grown up already and don't need that type of access restrictions. Or I'm wrong on this.

---

### Post by grumblebum2 on 2014-05-10
One thing I just came across is when I click on the launchpad link in the "about" window
firefox launches as root.

---

### Post by mjasnik on 2014-05-12
> **grumblebum2 said:**
> One thing I just came across is when I click on the launchpad link in the "about" window
firefox launches as root.

Well, this most likely is due to authenticating as superuser (root) + then by default sub processes are running with root as well. I'll try to look into the issue.

---

### Post by mjasnik on 2014-06-18
Hi!

I have run into translation problems. Whenever users are trying to use timekpr in previously translated languages - it just doesn't work. It seems that old translation files (mo files) are incompatible with newer gettext libs.
If You're familiar with translations You know that there are mo files which are compiled as binary for computer to use and there are po files which are human semi-readable and are used for translation with Poedit, Gtranslator or software like that.

I tried even with old versions of gettext but timekpr mo files can't be decoded into po files (it gives me error that strings are not NULL ended) and timekpr users are running into problems with old translations which lead into situation when timekpr settings just won't run at all.[B]
So here is the time I need Your help.[/B]

Please, if You are willing to contribute, send me an e-mail with language You're willing to translate to and I'll send You back the po file which You can translate using Poedit - that's easy.
Please mention the language here in forums, so ppl will know whether their language is already in translation. Please post only if You're giving it an effort and I can expect translation. There are ~ 70 messages to be translated.

So far I have Latvian (myself), French and Finnish translators already doing contribution. I can handle Russian as well if noone is contributing, but the rest is either google-translate which is kinda super fuzzy or I'll leave it as english, unfortunately.
**So if You use this software and are willing to see it in native language, please contact me.**

Thanks in advance.

regards
Mjasnik

---

### Post by mjasnik on 2014-07-01
Hi!

After some week I have 5 languages ready: Latvian/Russian myself, French - help from Canada, Finnish - help from Finland, German - help from Germany *(there are still problems in Timekpr due to German plurals, I'll try to fix them)*. Thanks to those guys, they will be mentioned in translation credits and Timekpr changelog.
Still not that much. So please, if You would like to translate - contact me. Only 70 messages ;) I'll try to fix previous mistake *(I'll post my e-mail here :)*), it's : edzis at inbox dot lv.

regards
Mjasnik

---

### Post by robert107 on 2014-07-01
I've always been looking for a decent parental control on Linux. Thanks for sharing.

---

### Post by mjasnik on 2014-07-05
Hi!

I have introduced plural forms in Timekpr, now there should be no problems with German language and others.
Simplified messages and fixed existing translations to use correct plural forms for each language.
New version ready for You to use.

So, still, don't be lazy, if You use Timekpr in other than 5 languages mentioned above and are willing to translate *(it's easy)*, please contact me. ;)

regards
Mjasnik

---

### Post by aleins on 2014-08-19
Hey Mijasnik,

it is great to have timekpr again. I use "the old version" with Xubuntu 12.04. I just installed Xubuntu 14.04 on an old machine for my son - and he need's timekpr!  I googeld timekpr and installed it like you described. It works perfect. I'm just a "normal" linux user and timekpr is a realy easy way of parental control.

Thanks a lot

Alexander

---

### Post by daniel-mcguire351 on 2014-09-12
I love this! It is fantastic!

If I could recommend one feature it would be integration with the Ubuntu Unity System Settings.

Keep up the awesome work!

---

### Post by mjasnik on 2014-09-15
Hi!

I have published version for Precise (12.04) as well. Testing shows it's working quite well, so please use it and if there are any issues - report them back.

regards
Mjasnik

---

### Post by aasche on 2014-09-22
A BIG thank you for your efforts in Timekpr! In the past there were different projects for parental control. Most of them are dead now. In my opinion one of the major failures Canonical produced in the past. Schools all over the world need two things: time restriction and access control to www. It's no secret children will later use things they had learned at school. But making short term profits seems to be more important than building a future with FOSS...

Back to topic: is there a chance to work together with the timekpr-maintainers at LP? At the moment there are 3 different PPAs and only experts know which one to use.

---

### Post by mjasnik on 2014-09-28
Hi,

Well, the instructions are on the first page of this discussion :)
As You notice original timekpr project is dead and that's why I started to maintain it in my ppa. My goal was to integrate into "main" timekpr ppa, but it's not happening yet.

I was not working on timekpr for some time as I have too much to do at my main work and timekpr was working quite good at least for my needs (and noone really complained about timekpr either), but now I have one developer helping me/introducing new features based on his own experience, so expect a new release with new features some time [hopefully] soon.

regards
Mjasnik

---

### Post by Bat on 2014-12-05
Looks like this one is dead too, now -- is it?  This is what I get when I try the apt-get update and install after setting up the ppa:

```
W: Failed to fetch [http://ppa.launchpad.net/mjasnik/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/mjasnik/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mjasnik/ppa/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/mjasnik/ppa/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
#####:~$ sudo apt-get install timekpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package timekpr
```

---

### Post by mjasnik on 2014-12-08
Hi!

Unfortunately packages for Utopic are not yet available. I was in the process on adding and testing new features like gtk3 / speech output (work done by German friend) but unfortunately regular work obligations took over.
I hope I'll add Utopic packages soon - at least in the current working state (speech output for certain languages like russian is not good at all (not friends fault), I have to fine-tune it to be usable at least).

regards
Mjasnik

---

### Post by mjasnik on 2014-12-09
Hi!

Utopic packages added, try it out. I haven't tested them myself, though.

regards
Mjasnik

---

### Post by dadour13-h on 2014-12-29
:~$ gksu /usr/bin/timekpr-gui
Error: Could not find timekpr section in '/etc/security/time.conf'
Button: setting an adjustment with non-zero page size is deprecated
:~$ 
can you assiste me i cannot use this software, i'm on edubuntu 14.04 lts, this software must install during installation of edubuntu>
please tell me how i can cure my problem and i looking for some similare program for internet control.
thank you

---

### Post by mjasnik on 2014-12-30
Hi!

Did You install timekpr via the ppa or .deb packages? Please write me an e-mail, let's not spam this on forums :)

regards
Mjasnik

---

### Post by Jonathan_Barton on 2015-01-06
Found an issue.
Using timekpr on Ubuntu 14.10. When trying to login with one of my kid's accounts, login does not happen. A message of wrong password displays. I login with my admin account and verify the kid's account with timekpr. The kid's account will be locked and displays that they have been on for hundreds of minutes, which is inaccurate as they were only on for the set amount of time. When the kid was on earlier and timekpr logged them out, the online time continued to accumulate even though they were logged out. So every time that one of my kids wants to log in, I have to first login to my admin account, reward them with enough minutes to bring them past the negative minutes plus enough for this time, log out of my admin account and then I can log them in.
So, 2 issues.
1) the error message when trying to login should display something showing that there is not enough time to log in, instead of the wrong password message
2) when the account is auto logged out, time should not continue to accumulate.

Many thanks in advance. Nice tool.

---

### Post by D_Sodelo on 2015-01-16
Hi,

I have the same problem than Jonathan, so I had to uninstall TimeKpr.
Would be very glad if this issue was corrected.
Many thanks.

---

### Post by mjasnik on 2015-01-23
Hi!

I did not test 14.10 myself, but I use 14.04 at home and nothing like "time is still accumulating after logout" happens, I have to get 14.10 to verify that, obviously. I'm not quite sure how many ppl are using 14.10.b
Do You run anything specific I should be aware of? Maybe not standard Ubuntu but Gnome flavour or so?

regards
Mjasnik

---

### Post by mjasnik on 2015-01-23
Hi!

And as for "login screen shows wrong password" seems to be login manager problem, it should say that account is blocked. Timekpr is using standard linux PAM methods of locking out user and if login manager shows wrong password instead of account blocked - I can't do much nor I want tbh. I can test console login though, how that respond to blocked account - haven't done yet :)
Children already know that when "invalid password" shows - it's due to lack of minutes and not wrong password :)

regards
Mjasnik

---

### Post by etyrnal2 on 2015-03-03
it's a little flaky.    In spite of the fact that i have set the time for users to be 180 minutes on weekends, 30 minute son tuesdays, and 120 minutes on the rest of the days, in the morning, if i log in to one of their accounts, it says 30 minutes available.  Last evening when i came home from work, i found out my one son couldn't use the computer the whole day because the machine said he had MINUS 900 minutes.  The number and variety of oddities are too much to list here.  I find myself constantly wrestling with it.  Same behavior across three machines.  One is 14.10 xfce (Ubuntu Studio?), one is 14.04 unity, one is 14.04 lxde.  They ALL require continual wrestling with it.  There's NO cli for it, and there's NO way to add time from WITHIN the user's account unless you want to spend unnecessary time opening a terminal, su to your own user, and running sudo timekpr-gui.  Why won't the GUI allow me to specify a user name with the password?  It's not likely am account with any kind of parental control is going to be an administrator account.  

Also, if one of the kids calls me and asks for more time, and i'm not home, if i ssh home, and shell to one of their machines, it seems there's no way through the cli to add time, or bypass, or unlock etc.  Would be cool of there were simple cli tools to :

$ timekpr add_time 60 jonny ronnie
$ timekpr bypass jonny
$ timekpr lock jonny suzie
$ timekpr reset_time jonny suzie
$ timekpr set_range sun 0700 2000 ollie susie frankie piere
$ timekpr set_range everyday 0700 2000 jonny suzy frankie kelly
$ timekpr show_status jonny teddy
$ timekpr show_status all

and others that would make sense.

thank you for reviving this project.  i'll be happier when it's stable.  for now, i'm wrestling my evenings away trying to make it work.  no fun.




p.s. it's awesome to see kids creativity spark back to life when they're put in a position of having to use their imagination again instead of being 'entertained' all day by irresponsible content curators.  They start doing healthy creative stuff again.


p.p.s.  what forum/mechanism is there to interact with the developers?

---

### Post by mjasnik on 2015-03-11
Hi!

Then I have to verify that myself as I have no such problems at all with 14.04 pure Unity, my main tester is my kid and he says all is good, so I believe him :)
Please do send me screenshots of configuration (Timekpr control panel), applet (how much time is reported to user in upper menu bar (at least in unity)) for every user You have problem with. Also please send screenshot of Your user accounts screen, so I can see which is admin user and which is not.
As for developers - there is just me (and one German friend who helped me a bit and ported GUI to GTK3 and stuff, it's not yet released), so there is not much to contact except me, edzis at inbox dot lv :)

> Why won't the GUI allow me to specify a user name with the password?
This is odd to be honest, check this - [http://www.webupd8.org/2014/09/install-timekpr-parental-control-app-in.html](http://www.webupd8.org/2014/09/install-timekpr-parental-control-app-in.html) (first screenshot), isn't that working on Your machines?
The thing is that timekpr-gui has to be run as root using either sudo or priviledged user, so I usually add time via the method described below, because for me that's faster, but You can login with administrator account and add time/reward using gui.

Also, there is a method how I remotely add time to my kids account - in /var/lib/timekpr there are files for every user, the .time file is what tells how much time left user have in seconds, so usually modify this file and user gets additional time.
Example: my kid has ONE hour every day, logon time is not restricted. So when time is over and I think he deserved more today, in .time file there is single line which reads about 3600, if I need to add half an hour, I change the line to 1800, that's it.

Also, in /etc/timekpr.conf there is configuration file, check LOCKLASTS variable, by default it says 30 minutes, if You decrease the time lock will last shorter. Also You can unlock the account using gui (Timekpr control panel).

regards
Mjasnik

---

### Post by dgutsche on 2015-03-17
Hello Mjasnik,

I'm happy to see timekpr is being revived!
I'm using timekpr to administer the accounts of my three daughters, and we have a special kind of problem. 
Every kid has its own computer, every computer has three accounts for every kid. (See where this is heading?) Plus one for school friends coming over for a game or two...
So if Kid One on Computer One runs out of time, it just switches over to Computer Two, where there is still plenty of time for Kid One...
I tried to fix this with the help of nfs-common (described this at the german ubuntu wiki):
1. install timekpr on every kid's computer.
2. copy (now) /var/lib/timekpr/* to a FORTH computer, preferrably one that is running while kids want to log in (we have a raspbian proxy server for this job)
3. export /var/lib/timekpr via nfs to each kid's computer, having rw-rights for root on this export

This prevents the kids from using their granted time three times, cause it will always write back used time to the same files (insert evil chuckle). Furthermore, you can start timekpr-gui on any computer, changes to the granted time will be globally accessible.

Except.
Except for time frames and account locks: as the time limitation and the account locking are realized via pam, and are carried out directly to /etc/security/time|access.conf, I can only lock accounts at the computer I'm currently invoking the timekpr-gui.
Since I do know programming, but not in python, I just felt my way through your code and came up with the following solution:
- delete variable TIMEKPRWORK, use TIMEKPRDIR for ALL user related files.
- use a $USER.lock-file for locking accounts. Use the timekpr-client.py to check for existence of this file. If existent, read its contents and write them into /etc/security/access.conf. If nonexistent for given user, erase given user from access.conf. $USER.lock will be created when button "Lock account" is clicked in gui. Second click will erase that file and set button to read "Account unlocked". As far as I can see, the timekpr-client will log out users based on access.conf
- use a $USER.limits-file for timeframes. Same here: check for existence, write over to /etc/security/time.conf, tell gui about it. 

Maybe out there are others like me who need a network based solution for timekpr. I don't have the knowledge to roll this into a neat ppa-package... but, obviously, you do.

So now I only have to find out why there are no changes to the userfiles in /var/lib/timekpr. Guess it's something to do with the nfs-setup, maybe not having sufficient rights...

Just my two cents,
dgutsche

---

### Post by etyrnal3 on 2015-03-19
i have same problem as above, but am administering manually for now...

here's my REAL problem...  every day i come home from work an ask the kids if timekpr let them login.  almost every day they say NO.

When i check what's going on, they almost always have hundreds, or thousand of NEGATIVE minutes. (like -1230)

i SUSPECT what is happening is that when they logout, or are logged out, some process of theirs is NOT killed, is left running, and shows them as 'using time', when in fact they are NOT logged in.

Is this possible?  It does it on 4 different computers.  Ubuntu 14.04, Ubuntu Studio 15b1 (xfce), UbuntuMATE 15.04, and another Ubuntu Studio 14.10 using xfce4 login...

something isn't right.

I have to get up every morning, login to every machine, and check to see who's timekpr says they have negative minutes, and reset them.

What's the problem, and how can i fix this from the CLI?  Sometimes i can ssh home and try to fix it, if i knew how.  Can i do it with a timekpr from the cli?  Or can i edit a flat file?  Can i write a bash script to reset their time?

if you want i can capture whatever file you'd need to understand what's going on

so, this morning i login to my administrator account...  was going to make sure the kid's times were reset, and unlocked...

they were at minus 300 minutes (NEGATIVE)...

so, i reset them (180 min for friday)...  they showed 180 min.

then i noticed, when i refreshed the settings, they said 179.

i double checked to see if there were ANY running background processes owned by the kids...  NONE.  (Viewing ALL processes)

Waited another minute...  refreshed...  178 minutes left...  HUH??

What's eating up their time?

this isn't making sense...

p.s. is this thread dead?  or are people not subscribed?

Which [COLOR=#000000]login manager does timekpr behave well with?


[/COLOR]

---

### Post by mjasnik on 2015-03-20
Hi!

I will look into it when I have time, definately smth is wrong. So I need to get XFCE version, Ubuntu Studio version and MATE version.
As I said previously no problems using standard Ubuntu 14.04.

This thread is not dead, I'm not subscribed either, I just look into it from time to time :)

regards
Mjasnik

---

### Post by etyrnal3 on 2015-03-20
> **mjasnik said:**
> This is odd to be honest, check this - [http://www.webupd8.org/2014/09/install-timekpr-parental-control-app-in.html](http://www.webupd8.org/2014/09/install-timekpr-parental-control-app-in.html) (first screenshot), isn't that working on Your machines?

regards
Mjasnik
  Yes, THAT works.  But when i launch timekpr-gui, WHILE logged into a child's account, i get the initial box asking me to authenticate, but it is ONLY asking for a password, and NOT a user. So, say my child is logged into their account, they have ten minutes left, and they ask me to add more time, if i try to launch timekpr-gui in their account, a dialog pops up asking for administrator password, but no opportunity is given to supply the dialogue with a USER.  So, i have to log them out, or switch user to add time.

---

### Post by etyrnal3 on 2015-03-20
i'm curious how the time winds up in the negative.

what is timekpr looking for to decide to subtract time?  as i mentioned, i watched timekpr removing minutes when a user was not even logged in, and system monitor showed no PIDs owned by that user.

---

### Post by mjasnik on 2015-03-22
Hi!

> i'm curious how the time winds up in the negative.

Well,  this can happen, timekpr does not log out user on the exact second time  has ended, so it still counting time and it can become negative. That's  why it says "LESS than 2 minutes" when logging out someone and when it  says that time is already over.
As I understood this was specifically  designed as grace period so that kid can save all open apps so he won't  be forcibly logged out w/o giving a time to save the stuff.

I'll  try to get those versions of ubuntu and check this, because my kid has  no that problem. One thing which confuses him though is that let's say I  give him an hour, exact hour, when he logs in he sees 59 minutes, and  it's because logging in takes time and timekpr already had counted some,  but after explaining that he was ok with it.

Can You please  observe that situation on standard Ubuntu 14.04 installation and send me  some screenshots excactly how You do it (with detailed steps written)?  It'll be hard for me to reproduce the problem cause currently it's  working for me. edzis at inbox dot lv

regards
Mjasnik

---

### Post by mjasnik on 2015-04-26
Hi all,

I found the problem which [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1975159")etyrnal3 is facing and it's directly related to using systemd. I have no problems whatsoever using 14.04 or 14.10 with upstart.
However 15.04 leaves user processes even user is logged out, that explains counting minutes even user is not really logged in.

Please check by yourself, run these 3 commands when minutes are counting but user is not logged and report back:
1. w
2. users
3. loginctl list-users

I didn't pay attention to versions used, but 15.0x is not yet supported by timekpr as there is no package built for it specifically! When it will be, this problem will go away!

regards
Mjasnik

---

### Post by mjasnik on 2015-04-26
Hi  dgutsche,

Idea is not bad at all, let's see how to implement that using very simple setup:
1. I don't really want to mount anything either using nfs/samba/...
2. I could make a configuration option with the destination on the network based of SSH/SFTP assuming there will be key-based auth to access that server/directory
3. The timekpr could operate on files remotely (I'll think how to do locking if multiple logins try to operate at the same time)
4. This way it could be quite ok to login from multiple computers as time could be managed in central location

Please let me know if this is ok or point out what is not good about my approach. Central management could benefit me as well :)

regards
Mjasnik

---

### Post by mjasnik on 2015-04-26
Hi all,

New version is rolled out, will be available as soon as it builds. Please test and report the issues.

Notable changes:
* administration now is possible via the indicator, there is new menu item
*  for administration purposes I'm using "pkexec" now, which for users mean  that password dialog will say which administrative user password is required and if  there are more than one administrative user, the list is presented, that's standard feature I can't change, but it works very well and is informative (etyrnal2 - solved ;))
*  user list is now retrieved using "w", "loginctl" and "users" are used as  fallback if "w" is not present, hopefully this will work better as  there were problems with user list using systemd/14.10 with it (etyrnal3 - solved ;))
*  notifications about time left are handled with critical severity which  means that they should show up even in fullscreen windows (frank - should be solved, please check ;))
* 15.04 support - it works for me, no intensive testing was done

Notice:  if You need quicker answer, please send me an email instead of  writing here, or write here and send me a notification email to check the  forum.

Hopefully I'll be able to add gtk3 support from Frank,  sort out text-to-speach issues for russian at least, so there will be  more options in the future.

regards
Mjasnik

---

### Post by etyrnal3 on 2015-04-26
[COLOR=#000000]Mjasnik, thanks!  Kids were going crazy =)  I can't wait to try it.

[/COLOR]For now, what is the preferred solution for using timekpr in a LAN?  (for now, i had just set the kid's time pretty low on each individual machine -- and they, of course, bounce around to different machines because of this - ha ha.).  (Kids are SO creative - i love that... until it's effects are a nuisance.)

It will be nice if someday, there would be, during install, or initial run, or from command line, or from timekpr-gui menu, an option to set up the nfs exports, or mounts at the click of a button.  Like three buttons maybe.  Button 1.) would toggle between local, or LAN setup,  Button 2.) (hidden until button one is pressed), could be, "Set up machine as network master", and button 3.) which could be, "Set up machine as network client."

When button 2.) is pressed, it would export the machine's /Var/lib/timekpr folder in /etc/exports...
when button 3.) is pressed, it could do a quick network discovery on the LAN for a list of machines, then allow you to select the one you want to serve as master, or lest you write in an IP, or hostname, and it would then modify /etc/fstab to mount that master machine's /var/lib/timekpr on the local /var/lib/timekpr...


or something like it.

just ideas.

This would also make remote cli management a little easier ... les ssh'ing around =) 

Thanks again! 


> **mjasnik said:**
> Hi all,

New version is rolled out, will be available as soon as it builds. Please test and report the issues.

Notable changes:
* administration now is possible via the indicator, there is new menu item
*  for administration purposes I'm using "pkexec" now, which for users mean  that password dialog will say which administrative user password is required and if  there are more than one administrative user, the list is presented, that's standard feature I can't change, but it works very well and is informative (etyrnal2 - solved ;))
*  user list is now retrieved using "w", "loginctl" and "users" are used as  fallback if "w" is not present, hopefully this will work better as  there were problems with user list using systemd/14.10 with it (etyrnal3 - solved ;))
*  notifications about time left are handled with critical severity which  means that they should show up even in fullscreen windows (frank - should be solved, please check ;))
* 15.04 support - it works for me, no intensive testing was done

Notice:  if You need quicker answer, please send me an email instead of  writing here, or write here and send me a notification email to check the  forum.

Hopefully I'll be able to add gtk3 support from Frank,  sort out text-to-speach issues for russian at least, so there will be  more options in the future.

regards
Mjasnik

---

### Post by etyrnal3 on 2015-04-26
i forgot to ask, to update, what do i need to do, just run the system software updater?  OR download a new .deb ?

---

### Post by etyrnal3 on 2015-04-26
figured it out.  updated apt-get, and installed timekpr.  i already see the new admin user panel allowing the selection of administrative user -- NICE!

---

### Post by mjasnik on 2015-04-26
Hi,

if You installed this via my ppa, software update should be enough.

regards
Mjasnik

---

### Post by ExNASATerry on 2015-05-01
First, thanks so much for reviving Timekpr!

My daughter isn't getting any popup warnings that her time is running out. She got quite upset when she lost about an hour of work on a paint project. (I've told her about making regular backups, but...)

I executed the following as a test and the message did pop up on her screen:

[COLOR=#333333][FONT=monospace]notify-send --icon=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gtk-dialog-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]warning --urgency=critical -t 3000 "test-title" "test-message"

Is she supposed to get a pop-up on login, too? Because if so, that's not happening either.

Any thoughts? Thanks again.

Timekpr 0.3.5 on Ubuntu 14.04LTS on a System76 SableTouch[/FONT][/COLOR]

---

### Post by mjasnik on 2015-05-02
Hi!

Sorry about loosing work...
When she logs in just right  after login she should get a popup saying how much time is left.
Actually timekpr does right that: notify-send.

Does timekpr icon shows up in the title bar when You/she login?
Is this a standard ubuntu installetion or MATE/GNOME/XFCE version?

regards
Mjasnik

---

### Post by ExNASATerry on 2015-05-02
I, the administrator, do have an icon; my daughter does not. We both use Gnome (Metacity).

---

### Post by mjasnik on 2015-05-03
Hi!

That's odd, can You create one more test user and login to check whether icon is shown in that users account?
Either way, You could add timekpr-client to daughters startup applications and it should run. So for gnome3 You need to use terminal, then enter gnome-session-properties, nice GUI will appear and then make new entry with the command timekpr-client. That's it.
But I really don't know why icon is not there for one user and is for the other.

regards
Mjasnik

---

### Post by ExNASATerry on 2015-05-05
That seems to have fixed it, thanks. One weird thing, though; when she first logs on in the morning, it immediately pops up _with the time remaining from the day before_. Yesterday, it said she had 2 minutes left; today it said she had 28. After about a minute or so, it resets to the correct amount and generates a new pop-up.

---

### Post by mjasnik on 2015-05-06
Hi!

I'm glad it worked out well for you...

Behavior of popups - well that is a bit inconvienent, but it's the way  it works. When user logs in, timekpr detects it just after max of 30  secs (default polling time) and then it resets the current state of the  user (if the new day has come - it has to reset the counter, etc.) and  second popup goes off with the correct amount for that day.
My kid  doesn't complain about it and I'm not sure if this is easily fixable,  all we can do currently is set polling time to smaller amount of time  which in one case will be more precise but there might still be delay  with the popup, but on the other hand - why we need to bother about some  30 secs :)

What I can do - disable the first popup, but I'm not sure that is needed.

regards
Mjasnik

---

### Post by daniel269 on 2015-05-06
Could anybody say something about this keylogger [COLOR=#1155cc][FONT=arial]_[http://www.refog.com/](http://www.refog.com/)_[/FONT][/COLOR] ?Is it reliable? I am on to download it , I currently use Android tablet and want to install good parental control software. Thanks.

---

### Post by Bucky Ball on 2015-05-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ExNASATerry on 2015-05-07
No, it's fine. Just thought I'd mention it. Thanks again!

---

### Post by ExNASATerry on 2015-05-07
> **mjasnik said:**
> Hi!

I'm glad it worked out well for you...

Behavior of popups - well that is a bit inconvienent, but it's the way  it works. When user logs in, timekpr detects it just after max of 30  secs (default polling time) and then it resets the current state of the  user (if the new day has come - it has to reset the counter, etc.) and  second popup goes off with the correct amount for that day.
My kid  doesn't complain about it and I'm not sure if this is easily fixable,  all we can do currently is set polling time to smaller amount of time  which in one case will be more precise but there might still be delay  with the popup, but on the other hand - why we need to bother about some  30 secs :)

What I can do - disable the first popup, but I'm not sure that is needed.

regards
Mjasnik

It's fine; just thought I'd mention it. Thanks!

---

### Post by maarts on 2015-05-25
Hi,

timekpr doesn't work with long user names. For example:

"heinzelong"

$ users
heinzelong

$ users.timekpr
heinzelo

--> /var/lib/timekpr/heinzelo.time

My system Lubuntu 12.04.

EDIT:

In /usr/bin/users.timekpr is first checked by w and w give a piece of the user name...

Thanks,
maarts

---

### Post by mjasnik on 2015-05-26
Hi!

Fixed, update rolled out.

P.S. I'm in the process of making timekpr as a revived / fork, so soon there will be a place to report bugs :)

regards
Mjasnik

---

### Post by maarts on 2015-05-26
Hi,

thanks!

Another question:

If a kids account exists, timekpr-client doesn't start. I tried with autostart, but nothing happens... If I create a new account, all looks good.

Do you have an idea? Or, how can I check, why it doesn't start?

Thanks,
maarts

---

### Post by mjasnik on 2015-05-26
Hi!

I have an idea, actually :) LXDE doesn't pick up autorun files from  /etc/xdg/autoruns, for some reason it just doesn't, so if You need to  run timekpr client for existing user (obviously You need that), please  add timekpr-client to startup programs manually.

P.S. If You find a solution which works automagically, please inform me as well, I'll implement that if that's possible.

regards
Mjasnik

---

### Post by maarts on 2015-05-27
Hi,

I find out the problem!


The permissions of the files in /etc/timekpr/ are not correct. Others doesn't have any read permissions...


After I remove all the files, timekpr-client starts on my existing kids accounts. The new files have the correct permissions.


I guess, that the first start with 'gksudo /usr/bin/timekpr-gui' set the wrong permissions.

Thanks,
maart

---

### Post by zeke2135 on 2015-06-14
This looks like an excellent tool. Thanks for keeping it up! Here is my one request: Would it be feasible to stop the timer when the kids are logged in but not active, as when the screen is locked or their sessions are in the background?

---

### Post by mjasnik on 2015-06-15
> **zeke2135 said:**
> This looks like an excellent tool. Thanks for keeping it up! Here is my one request: Would it be feasible to stop the timer when the kids are logged in but not active, as when the screen is locked or their sessions are in the background?

Technically there is a way to detect if the screen is locked, but every DM uses different method of screen lock which means that I need to know every of it to support it widely.
Timekpr daemon and client runs asynchronously, client just reports what daemon has counted, daemon runs under root which is not exactly the same user Ubuntu session runs, that just complicates things of detecting a screenlock, which is per user basis.
What I'm saying is - technically it's doable...

---

### Post by e-kevin on 2015-06-29
Hi Mjasnik,

Thanks for reviving this. I'm hoping this project can gain momentum.

Is it possible to fork your code?

Thanks!

---

### Post by mjasnik on 2015-07-01
> **e-kevin said:**
> Hi Mjasnik,
Is it possible to fork your code?


Hi,

first of all it's not exactly my code and You can take it, second I think there is no need to do any forks, there should be just one code on which everyone can develop timekpr. Not too far back I started to create account for having a code in launchpad, but didn't yet publish the code. I hope I'll do it soon and then everyone will be able to work on timekpr.
Hopefully this answers the question.

If You don't mind a question - why You need to fork the code?

regards
Mjasnik

---

### Post by e-kevin on 2015-07-02
> **mjasnik said:**
> Hi,

first of all it's not exactly my code and You can take it, second I think there is no need to do any forks, there should be just one code on which everyone can develop timekpr. Not too far back I started to create account for having a code in launchpad, but didn't yet publish the code. I hope I'll do it soon and then everyone will be able to work on timekpr.
Hopefully this answers the question.

If You don't mind a question - why You need to fork the code?

regards
Mjasnik

I've been looking for something similar to Qustodio, but for Ubuntu since I'm hoping to dump Windoze 8 on my daughter's laptop. This is the closest thing I've found, but I'd like to play around with the code and see if I can get it to read a configuration from a web service or something so it can be managed remotely.

---

### Post by mjasnik on 2015-07-10
Hi!

Great news :) I was able to create a new project in launchpad and from now on everything is there. Please ask questions/post ideas/register bugs and feature requests there, but before You do, please read the project description :)
Link: [https://launchpad.net/timekpr-revived](https://launchpad.net/timekpr-revived)

**Please note that**, due to different version strings now, if You don't get newest version automatically, please remove timekpr from Your computer and install it again. Sorry for this.

I hope, now contributions, if any, will be easy to handle.

regards
Mjasnik

---

