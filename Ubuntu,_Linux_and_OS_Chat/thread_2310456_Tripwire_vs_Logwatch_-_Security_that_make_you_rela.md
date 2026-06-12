---
title: "Tripwire vs Logwatch - Security that make you relax :-)"
date: 2016-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by patrikmellq on 2016-01-19
This is my opinion!

**The down side with Tripwire:**

With Tripwire i need to check the report each time before i change or update anything on my Ubuntu system.
And when install updates i have no clue if there will be an intrusion in the same time, so after installing updates i need to update the Tripwire database, but i can not be 100% sure that all changes that has been made is due the update install.
Maybe i am hard and the odds is not so big that a intrusion would happen exact the same time i make a Ubuntu Update or install a software.
This give me second thoughts about Tripwire. 

**The up side with Tripwire:**

I know how to install the Tripwire database on removable media, so no one can get into the Tripwire database.
You can also make a path for the security keys to be on removable media or usb stick.
This make Tripwire very secure.
This give me a very safe and secure feeling using Tripwire.
Only need to plug in the USB stick and run short command to get email report from the Tripwire database.

**The down side using Logwatch: **

The software is installed on your computer and running checks on your computer, it can be modified and tempered with or at least i think so as you don't can install Logwatch on removable media like Tripwire.

**The up side using Logwatch:**
You get daily emails reports with log files over your Ubuntu systems actions.And if you use sudo with wrong password you get a email alert in real-time**,** pretty cool.No need to do anything as all is running automatic.[B]

Here is the Tripwire Howto
[/B][http://ubuntuforums.org/showthread.php?t=2235300&highlight=tripwire+howto](http://ubuntuforums.org/showthread.php?t=2235300&highlight=tripwire+howto)[B]

Here is the Logwatch Howto [/B]
[http://ubuntuforums.org/showthread.php?t=2281615&highlight=install+logwatch](http://ubuntuforums.org/showthread.php?t=2281615&highlight=install+logwatch)


Conclusion:

I feel pretty secure using my Ubuntu with following solutions, UFW, VPN & LOGWATCHI feel i can relax and feel there is no need to be paranoid.

---

### Post by QIII on 2016-01-19
If you feel you can relax, you may want to reconsider.  Security is not a one-time setup, but a process of continuous re-evaluatiin and adjustment.

---

### Post by patrikmellq on 2016-01-19
So what are you saying? that a home user or desktop user that not run server has to monitor hes system with Tripwire, Logwatch, Chrootkit, Snort and so on ...
 Is not realistic, my opinion.

 At some point i have to stop being paranoid and have a common solution that will notice strange changes on system and then take action.
 Are you saying that we need more security solutions? then feel free to come with suggestion.

 As windows user you install Firewall and Virus protection, then you use your computer daily with no further action.
 At some extend you should have the same situation with Ubuntu.
 The task for a home user with desktop solution should not to build fortknox, if yes then i been wrong running Ubuntu.
 There has the be a cut point methodology where you can relax and in the same time make common observations.

 Correct me if i am wrong.
I can admit that i have the opinion that every Linux system should have Tripwire installation with database on removable media, but i feel to lazy for that.

---

### Post by Habitual on 2016-01-19
Do, or Do not, there is no "relax".

---

### Post by QIII on 2016-01-19
What Habitual said.  :)

What I am saying is that the threat environment, even for home users, changes continuously.

The "set and forget" Windows attitude is a good part of the reason Windows users get powned.  It's not a good example to follow.

---

### Post by patrikmellq on 2016-01-19
Do, or Don't do, there is no "relax" - he make a point but don't add anything to the discussion or come with any kind of explanation.
You also make a point - Windows attitude is a good part of the reason Windows users get powned - how should i understand that statment, that hackers/crackers have a easy time passing windows firewalls and virus detection systems?

My point above is not about if or if not you get hacked, because if some one want to make a intrusion there is nothing stopping them as i understand it.
My point is that there has to be some kind of path to follow, have a set up with certain security tools for observation of your system health - but then comes the question what should be common security measurements for home users with desktop.

What should you use and not overdue it!
Guide lines, for example Tripwire, Logwatch, UFW, VPN and Secure Firefox internet browser and have updated system.
Is that common measurements for a home user that browse internet, use email and play games or is that security measurements overdoing it.

---

### Post by Habitual on 2016-01-19
> **patrikmellq said:**
> he make a point but don't add anything to the discussion or come with any kind of explanation.
there is no "relax"  IS THE POINT.

---

### Post by buzzingrobot on 2016-01-20
These days, the most likely attack vector for the stereotypical home user is probably the browser, via malware disguised as ads. A user can run all kinds of traditional security tools and still invite trouble in with just a click. And, very often, not clicking.  Just loading the page passes on the infection.

Typically, the ads we see displayed on a site are not created and served by the publishers of that site. Instead, they come from ad syndicate operators that make, sell, and serve the ads, and then pay each site that displays them. 

The probem arises when someone manages to get an ad loaded with malware onto an ad syndicate's roster.  That ad -- and that malware -- will be served to every site using the syndicate, and then to every user who visits that site without an ad blocker. (And, since one approach to not displaying ads is to rebuild the page in memory after it -- ads included -- is downloaded by the browser, renoving the ads, I wonder if that's a sure thing.)

This isn't a problem that affects just the creepy side of the web.

---

### Post by maglin2 on 2016-01-22
> **Habitual said:**
> there is no "relax"  IS THE POINT.

True, but I suspect that '*I really wish I'd spent more time worrying about my OS logs*' is quite a rare deathbed speech.

---

### Post by QIII on 2016-01-22
Unless, of course, some nefarious and shadowy person breaks in, gets information they want and clears out your life savings - leaving you to eat cat food for the last 10 years of your life and have nothing to pass on to your children.

---

