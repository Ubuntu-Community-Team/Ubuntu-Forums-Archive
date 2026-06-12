---
title: "Ubuntu needs to be a revolving door"
date: 2012-03-05
forum: Testimonials &amp; Experiences
---

### Post by jadarite on 2012-03-05
A revolving door is the best analogy I can come up with to explain the main problem I am having with Ubuntu.

Ubuntu as an operating system is great.  However, not everyone uses Ubuntu/Linux, so we need to have better options and more to the point better methods to use other operating systems in conjunction with Ubuntu (like Mac and Windows OS).

First, some minor annoyances.  When I go to install Ubuntu, it just hangs.  I had to get Ubuntu back on my computer (I'll explain the problem later), and I had no idea the computer needed to be connected to the internet.  I thought putting it on the USB stick was enough.  It installed a few things then froze.  

Then, when I figured it needed internet access, things seemed to progress.  There was an orange progress bar.  It took a long time to get to what I hope was near the end.  I have no way of knowing because the orange bar would complete in stages and start over.  Eventually, it got to a point where it was trying to save something but I saw the modem flickering away.  I waited.  I waited some more, and I waited another 15 minutes.  No progress, no sign of anything happening.  As it is now, I probably still have to update more.  When I went to the update area, it came back with 440MB, about 220mb of it was suggested downloads.  I just wanted to get back on to Windows because I have some programs on there I needed to use.  So, apparently what it has done so far as given me back the GRUB and I can choose Windows like before.

Now the major pet peeve in all this.  I constantly have to select Windows when the computer boots.  It won't automatically go to Windows.  I can understand uninstalling an OS is not going to be an easy task, but come on guys, when we are at the GRUB menu, why can't we set the default OS so it always loads?  This seems like a plausible and easy thing to set up.

Here's the analogy, we need a revolving door.  This doesn't have anything to do with being an "expert" or "beginner".  If you wanted to enter a building, wouldn't you prefer a revolving door than having to unscrew certain bolts so the door will move the way you want?   Even if I understood the commands to get this sorted out, I would still want a quicker way to toggle the default OS.

In the end, if Ubuntu doesn't make this aspect more user friendly and incorporate some revolving door, then I only have one option: reinstall Windows and have it just reformat over the whole hard drive.  Whenever I have problems with Windows, then I can always put in Ubuntu.  That's how I can use Ubuntu as a backup.  This means I would less likely be using Ubuntu while Windows is working fine (which it has except for today's incident when I tried to remove Ubuntu so I could get Windows to automatically load).

I am not looking for a tutorial on commands which will change the default OS.  I am specifically requesting the programmers to put something in the GRUB menu option so we can assign a default OS there.  This seems like it would satisfy both the expert and the beginner.  I can't imagine any "Expert" preferring to type in commands when they could just move a selection up or down a list like that in the BIOS when we want to change boot up priority from hard drive to USB or CD.  

Doesn't that ability seem obviously more efficient in the end?  I hope sensible and practical people are reading this and can put this common sense approach to good use.  If you aren't one of the programmers, echo what I have mentioned to others in your circle.  Eventually, a programmer involved with Ubuntu is going to get wind of this and hopefully they will agree and do something about it.

With the stupid navigation bar thing on the left and this default OS issue, Ubuntu is becoming less attractive to the common user.  Before, options were along the top, now they are hidden behind windows.  It's rather frustrating trying to learn where everything I used to use is now placed.  This is partly why I just come back to Windows.  Everything is where it was back in Windows 98.  Very small changes like the audio settings can still be accessed in the lower right.

I guess my rant is almost over.  I just lost 7 hours of time which I had hoped to use for other things besides reinstalling Ubuntu so I could get the GRUB list back up so I could select Windows.  The reason why I did this is that my dad installed Ubuntu and had the same complaint.  I figured I should try to remove it first in case any problems came up, he probably would have a harder time getting the solution and have to take it to a repair shop where they would reformat it with Windows.

Please Ubuntu, make it easier on us to switch default OS settings.  Put some default toggle switch at the GRUB setting.  This will make it immensely more appreciated by those of us who don't care to learn commands or figure out where to type them.  Reading the help documents is like trying to sift through technical terms without any idea of what they refer to.  GRUB by itself sounds like either food from the cafeteria or mud a kid collects on their pants after playing in the rain.  Some of us users don't care what it really means, we have better things to do with our lives, but we appreciate the OS as it is.  We just want to have easier access to it and away from it.

---

### Post by whatthefunk on 2012-03-05
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

For a GUI alternative, try StartupManger:
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by nothingspecial on 2012-03-05
Moved to Testimonials.

If you do want help with any of the issues you raise, please start a thread for each one in the support areas.

Thanks :)

---

### Post by Grenage on 2012-03-05
> **jadarite said:**
> I am not looking for a tutorial on commands which will change the default OS.  I am specifically requesting the programmers to put something in the GRUB menu option so we can assign a default OS there.  This seems like it would satisfy both the expert and the beginner.  I can't imagine any "Expert" preferring to type in commands when they could just move a selection up or down a list like that in the BIOS when we want to change boot up priority from hard drive to USB or CD.

You are of course, correct; that said, Ubuntu has about as much control over Grub as I do over US policy.  They pick and use the fruit that makes the salad, but they don't grow the fruit.

---

### Post by Hikayu on 2012-03-05
Seems more like a suggestion than a request for general help. Unity, the "stupid navigation bar thing on the left," is optional, and not compulsory. With little effort, Unity can be replaced with the original GNOME 3 interface, the environment where "options were along the top".

Very true, Canonical has made Ubuntu more like the Vista of Windows recently. The Unity that was forced on since Maverick Meerkat. has been nothing but a disappointment to cope with. It should remain optional. Fortunately, the nearest LTS version, Lucid Lynx, still retains the good ol' GNOME 3 interface.

Linux, with the sole exception of Ubuntu, was never meant to accommodate Windows users with no intention of learning how it works or how it uses it. The analogy would be, Windows is the smelly taxi that takes you where you want for a hefty price, Ubuntu is automatic-transmission car and other distributions being the manual-transmission car. Unless you are willing to learn how to drive, you're just going to flounder helplessly with Linux. ;)

Sometimes, I can't understand Ubuntu's intention of trying to become all automated and user-friendly either. I guess this will improve with time, and frustrate both Linux-gurus and Windows-newcomers alike. A good compromise always leaves both parties frustrated, they say.

Seems like you probably already know how to set up the default OS with GRUB, but just didn't appreciate the number steps required. If you want GRUB to change, ask their developers. Suggesting this at an Ubuntu forum won't accomplish much, as the developers of the Linux kernel, the Ubuntu distribution, and the GRUB boot loader are completely different parties.

I apologize for the time you have lost trying to acquaint with the flexibility Linux offers on behalf of whoever you want to complain to, which is quite a broad party actually. It will take time, and unless you want all the fancy customization, turn back and go to Windows. It is easier to use for common-users and less frustrating if you don't mind re-installing it bi-yearly due to the accumulation of garbage and viruses.

---

### Post by jadarite on 2012-03-05
whatthefunk,

I know there is a method.  I am specifically asking that we have a menu option before it loads to set the default OS without needing to type any commands.  To be honest, I have looked at those instructions multiple times, and I don't fully understand them.  I would prefer an easier method.  Why can't it be set up to move the default OS to the top when the GRUB menu lists?  If you like this idea echo it to the people you know.

nothingspecial,

I am not asking for specific help where I would click the mouse or type something.  However, I am asking for help in the community sense where people would echo my idea and suggestion to put an option to set the default OS in the GRUB list.  Hopefully, a programmer involved with Ubuntu will hear about it and do something.

I don't fully understand the help documents and do you know how frustrating it is to try to explain those same help commands to a 75 year old father?  If I could just say "Click Windows" or "Click Ubuntu" and press enter, that would be a whole lot easier than what I see on those help pages.

Considering Ubuntu is supposed to be easy to use and geared for those with little to no knowledge about programming, common sense should ignite some neurons upstairs that yes indeed this is a help issue.  This would HELP immensely, just not a help issue where the user would type a command or click a bajillion icons to get one thing done.

---

### Post by jadarite on 2012-03-05
> **Grenage said:**
> You are of course, correct; that said, Ubuntu has about as much control over Grub as I do over US policy.  They pick and use the fruit that makes the salad, but they don't grow the fruit.


I don't fully understand.  I never had this problem until Ubuntu was installed.  So either they can change it directly, or they are using something else as a part of Ubuntu which puts the menu option there.  If it is the former, then the solution is in their hands.  If it is the latter, then they could echo my suggestion to those that make whatever part (grow whatever fruit) that puts the menu up to allow us to select a default OS.  To put Windows way at the bottom and Ubuntu at the top, me thinks Ubuntu has their hands in the cookie jar to some extent.  Is that just coincidence?

---

### Post by Hikayu on 2012-03-05
> **jadarite said:**
> whatthefunk,

I know there is a method.  I am specifically asking that we have a menu option before it loads to set the default OS without needing to type any commands.  To be honest, I have looked at those instructions multiple times, and I don't fully understand them.  I would prefer an easier method.  Why can't it be set up to move the default OS to the top when the GRUB menu lists?  If you like this idea echo it to the people you know.


As a community, it is your responsibility to convey the suggestion you want to the developer of the respective issue. We don't really pass on messages like a secret club.

> **jadarite said:**
> 
I am not asking for specific help where I would click the mouse or type something.  However, I am asking for help in the community sense where people would echo my idea and suggestion to put an option to set the default OS in the GRUB list.  Hopefully, a programmer involved with Ubuntu will hear about it and do something.


Our community comes from the mutual desire to have a working operating system. "Give and take". "I found a bug, here's the fix. Now make more content, I've helped you a bit". That sort of thing. We're not some close family that hand hold each other to the solution. We expect you to put some effort into getting there yourself. That's why we have lasted so long as an open-sourced community. This is essentially the same hierarchy *all* opensourced projects have.

> **jadarite said:**
> 
I don't fully understand the help documents and do you know how frustrating it is to try to explain those same help commands to a 75 year old father?  If I could just say "Click Windows" or "Click Ubuntu" and press enter, that would be a whole lot easier than what I see on those help pages.


Our manuals are just detailed and gets to the point. We do not expect complete technophobes to read them. Take some effort to learn the meanings, we live in an information-technology age and that will help you no matter how you look at it.

> **jadarite said:**
> 
Considering Ubuntu is supposed to be easy to use and geared for those with little to no knowledge about programming, common sense should ignite some neurons upstairs that yes indeed this is a help issue.  This would HELP immensely, just not a help issue where the user would type a command or click a bajillion icons to get one thing done.


No, no, no! That's what Ubuntu's been saying. Frankly, it has maintained that facade to a certain extent. It's DEFINITELY easier to use than other distributions, at the expense of flexibility. It is definitely good for people starting out. That's it. It is "supposed to be easy to use", but it's certainly not meant to be "geared for those with little to no knowledge about programming,". Where did you ever get that?

---

### Post by jadarite on 2012-03-05
> Seems like you probably already know how to set up the default OS  with  GRUB, but just didn't appreciate the number steps  required.Bingo, yes.  That's it exactly.  I learned html and  webdesign, but now that I can just use blog/word based sites to put my  content online and use template themes I can put my time to other things  than adding code.  The compromise allows me to do more of what I want.

On a side note, the Ubuntu One file storage service where you can store  5gb of files doesn't allow for you to move files to other folders.  This  is another example of non-user friendliness.  

> If you want  GRUB to change, ask their developers. Suggesting  this at an Ubuntu forum  won't accomplish much, as the developers of the  Linux kernel, the  Ubuntu distribution, and the GRUB boot loader are  completely different  parties.I think that if enough people see  eye to eye on this and there is eventually a meeting of the minds where  one big wig of the Ubuntu crowd and another of the Grub clan talk they  might actually come to an agreement that doesn't need a migrant Windows  user begging and pleading at the doorsteps of the GRUB mansion.

Hearing it through the grapevine can get things done.  I don't  necessarily expect a representative from Ubuntu to fill out a form and  follow some procedure implemented by the higher ups to get a common  user's voice heard.  The approach would be more along the lines of  someone reading this and talking to a programmer and that programmer in  turn talking to the GRUB family.  They are more likely to place greater  importance on it if a programmer using their stuff discusses and  requests the appropriate change.

Anyway, you have shown where the fence in all this is.  I will avoid  Ubuntu I guess until I really need it.  Perhaps there is another Linux  platform that alters things differently.  If not, linux will be the  backup only when Windows crashes (it hasn't for me since 95)

As far as viruses, I get very few with Windows that are at least  noticeable.  I had that USB virus issue 2 years ago where it would  rename files and make them disappear, but that seems to be fixed now.  I  put my USB stick and external hard drives into 18 different Windows  computers a week at the school I work at, and it hasn't been a problem.

---

### Post by wyliecoyoteuk on 2012-03-05
There is a simple solution really. 
Don't dual boot, and the problem goes away.
I only use Linux on my home PCs.
If you think that Grub is hard to use, you haven't tried using the Windows boot manager to multi-boot OSes.
Try suggesting to Microsoft that they should make it easier for people to boot other OSes and see how far you get.

---

### Post by jadarite on 2012-03-05
> As a community, it is your responsibility to convey the suggestion you want to the developer of the respective issue. We don't really pass on messages like a secret club.

If a restaurant serves cake, but they don't bake the cakes, we should complain to the company that bakes the cake instead of telling the waiter or manager?  I am specifically talking to Ubuntu because Ubuntu is the party using the part that I have an issue with.

If I were a programmer and I wanted to make my own operating system, then of course, I would go to GRUB.  This would be like the restaurant owner or representative going to one of their suppliers to request a change.

This has nothing to do with a secret club.  This is all out in the open.  It would make more sense to vote on important issues within the Ubuntu community and have programmers address them, either by making the changes themselves if they can or contact the parties capable of making the changes so their users can enjoy their product.  

> We expect you to put some effort into getting there yourself. 

That's an arbitrary line in the sand, there are plenty of upgrades to the recent Ubuntu that makes our effort as a user less confusing/frustrating when accomplishing a task.  

For example, I installed Ubuntu on an old imac, those colored ones you could carry and the hard drive was in the monitor.  This was back in 2003.  First, I could not use a USB stick (at least I didn't know how to), I had to put it on CD.  Now I can install it by using a USB stick.  The effort I put in is next to zero compared what I did in 2003.  I just download both files, install to USB, and reboot with the USB.  I don't need to get a CD, I don't even have a CD burner now, I don't need to use a CD burning program, etc....

Assigning a default OS would not only make our use of the computer easier with less stress, but we are more likely to use Ubuntu if we know we can toggle between the two.  With the hurdle of having to program in code, I would prefer to just reinstall Windows and get Ubuntu when I really need it.  

Think of it like a partition.  If I am a Windows user, I will use it 80% of the time, Ubuntu 20% of the time.  As I use Ubuntu more often, that ratio will be 70% to 30%, then 60% to 40%.  I still need to toggle between the two operating systems though.  Even if it goes to 1% to 99%, I still need to be able to toggle between the two.  

It's in Ubuntu and the community's best interest to listen to people like me who enjoy both Windows and Ubuntu.  There are plenty of posts online where people either want to remove Ubuntu to save space or change their default OS.  Instead of flinging code in our faces, please think of a different solution.  

> Take some effort to learn the meanings, we live in an information-technology age and that will help you no matter how you look at it.

I already spend the day learning Chinese, Korean, Japanese, teaching Asians in those languages, and teaching those languages through online classes.  I know we can all benefit by learning one more language, one more definition, one more formula.

However, at some point, if you want to move on you need to say goodbye to other things.  I could learn how to make my own pants and then I wouldn't have to buy them.  That just takes time, and I really don't care if I have to type "/Default OS change to Windows on Tuesday" or "Default bootrec.exe Tomorrow to Ubuntu please with sugar on top".  I am not interested in learning all the nuances of an operating system.  I just want to turn the key and drive.  Do you understand what I am getting at?  Where's the on and off switch.  Make it easy for us, making it password protected with commands is daunting to most who come home after a hard day's work and just want to enjoy themselves.  

Do you want Windows to win in this regard?  I just put the Windows CD in and there is no GRUB.  It automatically gets me to my files and online in no time.  I am using it now to post here, and I have no idea what more Ubuntu needs installed.

> it's certainly not meant to be "geared for those with little to no knowledge about programming,". Where did you ever get that?

Considering poor countries that can't afford an OS would use Ubuntu, those users are not likely to know or have experience with computers.  The iphone is marketed in a similar fashion where people don't need to know about programming to get phone calls and internet access through one small device.  

To say Ubuntu is only for the "geek" world would really undermine the attempts I see for everyone young to old (with limited computer skills) to use an operating system which is affordable and easy to understand.  Adding commands to make things easier is a backwards approach to user-friendliness.  It is indicative of an area that can be improved upon.

---

### Post by whatthefunk on 2012-03-05
With the amount of time youve spent complaining about this problem, you could have switched the default OS a thousand times....

---

### Post by jadarite on 2012-03-05
> With the amount of time youve spent complaining about this problem, you could have switched the default OS a thousand times....     You are missing the bigger picture.  Whether or not I could do it 1 time or 1,000 times is not the point.  My father, my stepmother, friends who can't understand the pages would not be able to.  That's why I did it first.  I figured if I run into problems then I need to see what is involved to fix it because they will have to as well.

To give you an idea, my father uses AOL email still and I tried sending an email with the help instructions.  He could not get the email.  For some reason it's not getting sent.

step 1 : Insert the Windows 7/vista/xp DVD and restart your computer.
step 2 : Go to recovery windows/console and execute the following command(s) :
bootrec.exe /fixmbr
bootrec.exe /fixboot
step 3 : Now, remove the installation disc, restart the computer and format ubuntu partition (ext3/4 file system) to a windows file system such as NTFS or FAT. 
 
step 4 : That&#8217;s All. You are Done!

(We couldn't understand step 2, there was no recovery windows console, we were lost at that point.)

Also, I am in China, so things are very slow here.  It takes about 10 minutes for something when it normally takes 1 second in the states.  Google doesn't load fast, and I have wait a long time to get email to work.  Downloading Ubuntu is a major pain because it takes up all my bandwidth and I can't get anything done.

I understand if things might be perfect in your world and I shouldn't complain.  Not all of us live with a fast internet connection and know commands.  I still have to prepare classes for this week and that is what I planned to do today 10 hours ago, but because this came up I haven't been able to.  I have had to find a fix.  I am complaining with reason I feel.

If you can't see the positive side to communicating this with others, then by all means bow out.  Let those with programming skills work towards a solution to make this easier for users.

---

### Post by whatthefunk on 2012-03-05
But they already have.  Have your tried StartupManager??

---

### Post by jadarite on 2012-03-05
> If you think that Grub is hard to use, you haven't tried using the Windows boot manager to multi-boot OSes.

Well, you could just pop a Windows CD in and reinstall or reformat.  I don't happen to have a CD drive on my computer. 

I don't see how it is that difficult.  If you can set a BIOS setting to toggle between USB and hard drive, why couldn't you set a default OS?

I understand you are preaching the way things are and I am preaching the way things could be.  But with issues as I listed above, even when you have commands, it doesn't always work.

I was able to reinstall Ubuntu to a point where it is asking for 400+ more mb of download, which is like 2-3 hours here in China.  Instead, I restarted the computer and it brought the GRUB list. 

I understand the commands are easy for you guys who type them out a lot.  However, I am not a programmer and I just want to get something running quickly so I can do my other stuff.

---

### Post by Tamlynmac on 2012-03-05
[> ]("http://ubuntuforums.org/member.php?u=1162346")[jadarite]("http://ubuntuforums.org/member.php?u=1162346")
Ubuntu as an operating system is great.  However, not everyone uses  Ubuntu/Linux, so we need to have better options and more to the point  better methods to use other operating systems in conjunction with Ubuntu  (like Mac and Windows OS).

In my opinion this is  corrupted logic. Why is it only Ubuntu's or Linux's responsibility to  integrate (dual boot) with another OS. Why haven't you gone to MS/Mac  and complained that they aren't making an effort to integrate with  Linux? Ubuntu/Linux is stand a alone OS and not a Windows or Mac clone.

The  concept that one group is obligated to assure integration with the  product of a competitor without a combined effort - seems foolish. I'm  often surprised when a user comes here to complain that Ubuntu/Linux  doesn't play well with Windows or that somehow it's Linux's  responsibility to assure Windows functionality in a dual boot  environment. Seriously?

I liked to suggest you contact MS/ Mac  and complain about dual boot integration with Linux and ask them what  they plan to do about it. Then come back and share with us their  reaction. Please don't respond with which OS has a larger base or is  more recognized, when your expectations for solutions are targeting  Linux only. Which group has more resources to invest in the effort? I  suspect many of us will be extremely interested in any responses you  receive from MS or Mac regarding this issue. :wink:

You state that not everyone uses Ubuntu/Linux, but then again not "everyone" uses Windows or Mac either.

Just my $0.02

---

### Post by QIII on 2012-03-05
1.  Ubuntu devs don't hang out here.  Wrong venue.

2.  GRUB devs don't hang out here.  Wrong venue.

That you can dual boot AT ALL is something to cheer to the GRUB devs about.  If, however, you would like some further functionality, that is something to suggest to them.

What you are saying is not without merit.  Where you are saying it is probably wasting your time.

For just a moment, analyze your compaint.   

For you to dual boot, whatever your default, three to five seconds must be allowed for selection of the non-default.  So, for the default, you may wait three to five seconds or press enter.   One keystroke.  In the same three to five seconds, you can hit the down arrow three times and press enter.  Four keystrokes.

I don't know about you, but in my sixth decade of life you can imagine that I have become accustomed to many greater irritations.

---

### Post by xaegis on 2012-03-05
I'm not trying to be offensive here but seems as though your perspective has become a bit skewed. This is a situation where honesty comes into play. 
When ones reach exceeds ones grasp one either puts the extra effort in to fill the gaps in their information and tool-set or one pays someone else to fix the issue for them. 
Computers are very complex machines, there are going to be situations which is is conceivable that a person, regardless of age, will find himself in over his head. In this case it is important to realize that sometimes one needs to lean on their support structure or pay for technical support if you are unable to access or understand the free help which is offered. This is not a failing of Ubuntu but the nature of the complexity of our tools and our quickly moving technological society. 
As an opposing use case setting the default OS in Ubuntu is much easier than setting up a static IP to access a hidden network in Win 7. There are many possible scenarios when it would behoove one to seek professional help. It seems as though with your busy schedule you might benefit from having a "go to guy” to help with your computer setup as well. The cost in (money or barter) of retaining someone to do this for you would be minimal compared to your lost productivity and headaches. 

just my $.02

---

### Post by mikewhatever on 2012-03-05
> **QIII said:**
> 1.  Ubuntu devs don't hang out here.  Wrong venue.

2.  GRUB devs don't hang out here.  Wrong venue.

That you can dual boot AT ALL is something to cheer to the GRUB devs about.  If, however, you would like some further functionality, that is something to suggest to them.

What you are saying is not without merit.  Where you are saying it is probably wasting your time.

For just a moment, analyze your compaint.   

For you to dual boot, whatever your default, three to five seconds must be allowed for selection of the non-default.  So, for the default, you may wait three to five seconds or press enter.   One keystroke.  In the same three to five seconds, you can hit the down arrow three times and press enter.  Four keystrokes.

I don't know about you, but in my sixth decade of life you can imagine that I have become accustomed to many greater irritations.

Exactly!

---

### Post by snowpine on 2012-03-05
Editing GRUB options is a root-level operation that can only be performed once the system is booted, the user is logged in, and authenticated with sudo. Allowing Grampa to change GRUB options pre-login without a password would be a security hole.

---

### Post by Peripheral Visionary on 2012-03-06
Perhaps Ubuntu *is* a "revolving door" in a good way. I've lurked in these forums for a long time before I finally joined, and I read many threads that describe different kinds of users. There's the "casual" user for whom the computer is just an appliance, who doesn't care to learn all it's inner workings other than routine maintenance.

There's the "casual geek" - the casual user who discovered his or her "inner geek" when they installed or reinstalled Ubuntu. Ubuntu encourages casual users like me to take their first steps into the wonderful world of geekdom. Now at this point, a user who has bravely taken those first few steps and liked it, or found it "not so bad," will continue and perhaps eventually move on to other Linux distros and perhaps return to Ubuntu again as a code contributor or developer or something. Revolving door. Or he may decide to go back the other way and remain a "casual user." Either way is okay.

Ubuntu isn't for super-geeky brainiacs either, but even super-geeky brainiacs use it because it's

a) awesome
b) easy to share with Grandpa
c) fits on a single LiveCD for bringing to school
d) easy to offer "tech support" for non-geeky Grandpas and schoolmates.

Revolving door? So what? That ain't a bad thing.

---

### Post by rg4w on 2012-03-06
> **jadarite said:**
> You are missing the bigger picture.  Whether or not I could do it 1 time or 1,000 times is not the point.  My father, my stepmother, friends who can't understand the pages would not be able to.
Respectfully, your are missing an even bigger picture:  without you on board, would it every occur to any of those people to replace the OS that came with their computer with something they downloaded from the Internet?

Linux has a much harder job than Mac or Windows because both of them have computers designed specifically to run them, and the OS is pre-installed.

Here you offer an excellent example of how challenging computers can be even in the best of circumstances:

> To give you an idea, my father uses AOL email still and I tried sending an email with the help instructions.  He could not get the email.  For some reason it's not getting sent.

step 1 : Insert the Windows 7/vista/xp DVD and restart your computer.
step 2 : Go to recovery windows/console and execute the following command(s) :
bootrec.exe /fixmbr
bootrec.exe /fixboot
step 3 : Now, remove the installation disc, restart the computer and format ubuntu partition (ext3/4 file system) to a windows file system such as NTFS or FAT. 
 
step 4 : That&#8217;s All. You are Done!

(We couldn't understand step 2, there was no recovery windows console, we were lost at that point.)There we see that even with a computer designed specifically for Windows, one that has a dedicated recovery disk designed exclusively for it, recovery was made difficult because of obscure command-line requirements.

Sometimes computers get complicated. ;)

If you want a good experience at least on par with other OSes you'll want to get a computer  with Ubuntu pre-installed, e.g. System76, ZaReason, LinuCity, or if  outside the US Asus, Dell, and others offer some models in certain markets.

To have a great experience with another computer, consider buying from this list of certified hardware:
[http://www.ubuntu.com/certification](http://www.ubuntu.com/certification)

It's a wonderful testimony to the value of FOSS that Linux runs on nearly every machine made in the last decade.  Some work better than others (I've been lucky in that all of my installs have been out-of-the-box successes), and once in a while you'll come across some combination of hardware for which finding drivers will be challenging.

But consider this:  Ubuntu has about 20 million users, and the number of support issues raised here is much smaller than 20 million.  It's working great for most people, and even in the worst case it's very rare that it can't be made to work with nothing more than a few lines in Terminal.

Most of all, with relatively few exceptions Ubuntu is being used on machines designed for an entirely different OS.

Not so bad, really, when you consider the challenge it has.

And all the while, Canonical is working with OEMs to increase the number of computers that have Ubuntu pre-installed.  THAT's what will make the biggest difference of all in terms of simplicity of the user experience, just as it has for every other OS.

---

### Post by leclerc65 on 2012-03-06
> I am specifically requesting the programmers to put something in the GRUB menu option so we can assign a default OS there. 
You can customize Grub menu easily with 'grub-customizer':
[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

---

### Post by 3rdalbum on 2012-03-08
I'd agree with the OP that it must be easy to change the GRUB menu; editing a text file shouldn't be the only way.

However, I disagree with the OP that this method necessarily has to be at the GRUB menu itself, and I disagree that the current method is too difficult. You can easily locate and install software from the repositories to allow you to modify GRUB settings, and I think it's best that Ubuntu doesn't come with this kind of software by default. You'd have people playing around with the GRUB menu without understanding what it is or how they could stop their system from booting.

---

### Post by wyliecoyoteuk on 2012-03-08
> **jadarite said:**
> Well, you could just pop a Windows CD in and reinstall or reformat.  I don't happen to have a CD drive on my computer. 



I don't think that you understood me.
It is possible to boot multiple OSes using the Windows bootloader instead of grub, but it is definitely not as easy as Ubuntu makes it.
Nothing to do with CDs or reinstalling.
You are complaining that Linux doesn't make it easier to dual boot with Windows.
Surely that is a Microsoft problem?
Ditch Windows, problem solved.
Maybe if you still need Windows, you don't need Linux.

---

