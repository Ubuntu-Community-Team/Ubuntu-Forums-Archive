---
title: "DCP-7065DN Brother printer install in 14.04 xubuntu"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by goodbye-windows(tm) on 2014-03-03
Hi All,

I'm trying to make my new printer run in 14.04 Daily Build (xubuntu). 

The installation instructions are here:

[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/dlf/000000/005400/dlf005483.html?reg=us&c=us&lang=en&prod=dcp7065dn_all&type2=91&os=128&flang=4&dlid=dlf005483](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/dlf/000000/005400/dlf005483.html?reg=us&c=us&lang=en&prod=dcp7065dn_all&type2=91&os=128&flang=4&dlid=dlf005483)

In step 3, I am asked to check for and install a 'Pre-required Procedure', **lib32stdc++**

Note that this appears to be a 32 bit program, I'm using a 64 bit system-not sure if this is an issue or not.

When I attempt to install lib32stdc++, I get the following error:

```
root@ofourdaily:/home/ofourdaily# apt-get install lib32stdc++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'lib32stdc++6-4.4-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.5-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++-4.8-dev' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.0-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.6-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.1-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.7-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.7-dev' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.2-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.8-dbg' for regex 'lib32stdc+'
Note, selecting 'lib32stdc++6-4.3-dbg' for regex 'lib32stdc+'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lib32stdc++6-4.6-dbg : Conflicts: lib32stdc++6-4.4-dbg but 4.4.7-5ubuntu1 is to be installed
 lib32stdc++6-4.7-dbg : Conflicts: lib32stdc++6-4.4-dbg but 4.4.7-5ubuntu1 is to be installed
                        Conflicts: lib32stdc++6-4.6-dbg but 4.6.4-6ubuntu1 is to be installed
 lib32stdc++6-4.8-dbg : Conflicts: lib32stdc++6-4.4-dbg but 4.4.7-5ubuntu1 is to be installed
                        Conflicts: lib32stdc++6-4.6-dbg but 4.6.4-6ubuntu1 is to be installed
                        Conflicts: lib32stdc++6-4.7-dbg but 4.7.3-11ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
root@ofourdaily:/home/ofourdaily#
```

After this error, I cannot proceed with the instructions is step 4. 

I did try this in one of my other installs (12.04), it didn't work but I didn't document the specific errors.

Is this error due to me running the pre-release version of 14.04 Xubuntu, or should I be looking for instructions for the 64 bit version?

TIA

Art

---

### Post by Frogs Hair on 2014-03-03
***Moved To Ubuntu +1***

---

### Post by goodbye-windows(tm) on 2014-03-03
Just after I posted this message,. I installed 12.04 to test with, and got the same exact error. I also used Google to search for the specific wording of the error and found another user ( post on facebook at [https://www.facebook.com/permalink.php?id=459650527418610&story_fbid=397216790368807](https://www.facebook.com/permalink.php?id=459650527418610&story_fbid=397216790368807) ) running 12.04 and having the same error. 

SO, it's not likely this is a 14.04 related error. Please move this thread back to its original category, I will edit the thread to remove most of the refrences to the 14.04 Daily Build installation.

Thanks,

Art

---

### Post by goodbye-windows(tm) on 2014-03-04
Please delete this thread. My other 12.04 installations have the same issue, so it's NOT an issue/bug specific to 14.04!!!

And, for anyone who actaully reads this.....

**14.04 runs circles around 13.10!!!!** The mesa video drivers work properly, the built in wireless in my Dell laptop now works!!!! And the severe stability issues in 13.10 (frequent unexpected applications closing doesn't happen in 14.04).

I'm using 14.04 on all my computers (1 desktop with AMD 6 core processor and 1 laptop with an I5 processor....total of 6 Xubuntu installations, 2 are 12.04 and 4 are 14.04). **14.04 is a real workhorse!!**

The only issue with 14.04 is that a launcher for the home folder cannot be created in an added panel....when I look at the list of launchers I can add to a panel, the shortcut/launcher for the 'home folder' is not present.

_**I am overjoyed with 14.04 and can't wait for the official release in April.**_

Art

---

### Post by Frogs Hair on 2014-03-04
Closed per request.

---

