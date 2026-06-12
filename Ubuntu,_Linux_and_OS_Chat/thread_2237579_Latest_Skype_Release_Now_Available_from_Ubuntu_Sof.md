---
title: "Latest Skype Release Now Available from Ubuntu Software Center"
date: 2014-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by philinux on 2014-08-02
Quote:-
The result for those unwilling to &#8212; or unable to &#8212; upgrade is drastic:*older versions of Skype will stop working;*they won&#8217;t be able to sign into, access features of, or connect with users on*the service.

[http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/08/install-skype-linux-4-3-ubuntu-software-center?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by mn_voyageur on 2014-08-02
FYI - I was unable to install Skype via the software center.  I had to run sudo apt-get install skype.

MarkN

---

### Post by philinux on 2014-08-03
> **mn_voyageur said:**
> FYI - I was unable to install Skype via the software center.  I had to run sudo apt-get install skype.

MarkN

Did you raise a bug report against software center. Any errors you noticed etc.

---

### Post by V_Lnh_Ti on 2014-08-03
problem herer: install error? 
i try restart and reinstall and
[COLOR=#000000] sudo apt-get install skype
its ok.[/COLOR]

---

### Post by philinux on 2014-08-03
Quote from link in post #1

The latest stable release of Skype for Linux is*now available*to install from the Ubuntu Software Center on 12.04 LTS and 14.04 LTS.*

---

### Post by shantiq on 2014-08-05
[COLOR=#000000]using 13.10 myself I was faced in the last few days with ```
skype cannot connect!
``` message


thought it was a personal issue


reading around it says 4.2 has been "decommissioned"   and we need 4.3 instead

tried a few suggested routed and debs to no avail


then found this [/COLOR][[COLOR=#000000] here[/COLOR]]("http://askubuntu.com/questions/488053/how-to-install-skype-4-3/507288#507288")[COLOR=#000000]


and this suggestion did the trick    may be of use to others too

[/COLOR]```
[COLOR=#000000]sudo apt-get install sni-qt:i386 /[/COLOR]
[COLOR=#000000]wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64 -O /tmp/skype-ubuntu-latest_i386.deb && sudo dpkg -i /tmp/skype-ubuntu-latest_i386.deb[/COLOR]
[COLOR=#000000]sudo apt-get install -f[/COLOR]

```[COLOR=#000000]
[/COLOR]

---

### Post by coffeecat on 2014-08-05
Merged with existing thread.

@shantiq, your 13.10 installation is now end-of-life and unsupported. You need to be running 14.04. As you can see from earlier posts in the thread I've merged yours into, skype 4.3 is available in the Software Centre in 14.04.

---

### Post by shantiq on 2014-08-06
Thanx Coffeecat   i was aware of the availability of 4.3 in 14.04 .    My thread was really for folks who are still,  like myself, for one reason or another [maybe waiting for 14.10] with 13.10     and wish for skype to function  ;    but if the info is seen here too   fine then

---

### Post by SUPERFITTER on 2014-09-25
I'm running Ubuntu 14.04. I went to the software center to get the new version of Skype 4.3.0.37.  I removed the old version and installed the new version.   When I load Skype it says Skype 4.2 for Linux and I cannot sign into Skype.  It says  !Skype cannot connect.

I ran software updater, there was a 20.1mb update for Skype that I updated. I rebooted and all is well now

---

### Post by Habitual on 2014-09-25
> **SUPERFITTER said:**
> I'm running Ubuntu 14.04. I went to the software center to get the new version of Skype 4.3.0.37.  I removed the old version and installed the new version.   When I load Skype it says Skype 4.2 for Linux and I cannot sign into Skype.  It says  !Skype cannot connect

Log out of Skype. Make sure it's not running. Close, Exit Skype.
Open File Manager, and press Ctrl+H to show hidden files.
Rename .Skype in your home directory to anything.

Launch Skype.

Report the results.

---

### Post by shantiq on 2014-09-26
or if Habitual's workaround is not successful on your system try [this]("http://ubuntuforums.org/showthread.php?t=2237579&p=13091314#post13091314")

---

### Post by SUPERFITTER on 2014-09-27
> **Habitual said:**
> Log out of Skype. Make sure it's not running. Close, Exit Skype.
Open File Manager, and press Ctrl+H to show hidden files.
Rename .Skype in your home directory to anything.

Launch Skype.

Report the results.

I ran software updater, there was a 20.1mb update for Skype that I updated. I rebooted and all is well now, I have                  Skype 4.3.0.37 now.

Thanks for the help

---

### Post by Habitual on 2014-09-28
Glad it worked out!

---

### Post by Tar_Ni on 2014-09-29
The most popular Linux apps should be found in the Software Center, so I am happy with this decision. The Mint project have a similar approach, Skype can be found in the software manager.

Now what about Chrome in the Ubuntu Software Center? Must be the most popular proprietary Linux app available. Though to be fair 90% of Chrome's source code is in fact, open-source.

---

