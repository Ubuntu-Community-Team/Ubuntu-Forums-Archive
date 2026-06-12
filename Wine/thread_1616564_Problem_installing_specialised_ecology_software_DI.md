---
title: "Problem installing specialised ecology software DISTANCE in Wine"
date: 2010-11-08
forum: Wine
---

### Post by trsr on 2010-11-08
Hi,

I'm new to the forums and have a problem installing a specialised ecology software on Wine to run on Ubuntu. Ever since I switched to Ubuntu, I've completely stopped using Windows and this software that I need to use, called DISTANCE 6.0, is written only for Windows: [http://www.ruwpa.st-and.ac.uk/distance/](http://www.ruwpa.st-and.ac.uk/distance/). I downloaded the setup file d60setup.exe for Windows XP.

I'm running Ubuntu 10.10 (64-bit) as the sole OS on a Dell 1558 laptop. When I try to install the d60setup.exe file using Wine I get the following message:

> 
Distance Internal Error
The following internal error has occured in Distance:
Jet VBA file (VBAJET.dll for 16-bit versions, or VBAJET32.dll for 32-bit versions) is missing. Try reinstalling the application that returned the error.

(Error raised from: DIstance.ModMain.Main)
(Error source: DAO.DbEngine)
(Error number: 3446)

If you suspect that this error is caused by a bug in the program, please note down all of the above information and contact the program authors.

Press Ok and Distance will try to recover from the error.
Press Help for more information about internal errors in Distance.

I would greatly appreciate any advise on how to fix this and use this software in Ubuntu linux. I really do not want to have to install Windows just to run this one software.

Thanks and cheers,

trsr

---

### Post by lsmobrian on 2010-11-09
Are you familiar with winetricks?  You might need to install some extra stuff using that.

```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
./winetricks
```


Then scroll through and look for JET40.  There could possibly be other things needed, jet40 is the only thing in the list that sticks out

---

### Post by trsr on 2010-11-11
> **lsmobrian said:**
> Are you familiar with winetricks?  You might need to install some extra stuff using that.

```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
./winetricks
```


Then scroll through and look for JET40.  There could possibly be other things needed, jet40 is the only thing in the list that sticks out
This is excellent lsmobrian, thanks! I used winetricks and installed the JET40 and the program now opens without a hitch. I've been able to rerun old data files/analyses. Hopefully, it should also work with new data entry and analysis as well. Will report back if I run into any other stumbling blocks. But your suggestion was really useful--much appreciated!
Cheers,
trsr

---

### Post by Simbamangu on 2011-05-27
Hi trsr - I've been struggling with the same issue, installing DISTANCE 6.0 in Wine, and was really excited to see this posting!

However, I am failing to get DISTANCE to run after installing JET40 in Winetricks (Wine 1.3). I continue to get error messages when I open a file or try to set up a new one: "The following internal error has occurred in Distance: Object doesn't support this property or method. (Error raised from: Distance.ClsProject.IsOkToOpenProject) ...".

(I've tried this with wine 1.2 on Mac OSX 10.6 with the same result).

Did it simply run perfectly for you, no error dialogs?

Thanks!

Ubuntu 10.10 with Wine 1.3 and Winetricks.

---

### Post by trsr on 2011-05-28
> **Simbamangu said:**
> Hi trsr - I've been struggling with the same issue, installing DISTANCE 6.0 in Wine, and was really excited to see this posting!

However, I am failing to get DISTANCE to run after installing JET40 in Winetricks (Wine 1.3). I continue to get error messages when I open a file or try to set up a new one: "The following internal error has occurred in Distance: Object doesn't support this property or method. (Error raised from: Distance.ClsProject.IsOkToOpenProject) ...".

(I've tried this with wine 1.2 on Mac OSX 10.6 with the same result).

Did it simply run perfectly for you, no error dialogs?

Thanks!

Ubuntu 10.10 with Wine 1.3 and Winetricks.
Yes... it worked without any further error messages at that time. Cheers

---

### Post by Simbamangu on 2011-05-28
Which version of Distance did you use? I see you mentioned v6, but which release?

DId you install anything else within that same Wine prefix?

---

### Post by trsr on 2011-05-28
| Which version of Distance did you use? I see you mentioned v6, but which release?
Er... sorry, I've since uninstalled that and moved on to Ubuntu 11.04... so I'm not sure.

| DId you install anything else within that same Wine prefix?
Not that I recall, no.
Sorry that I unable to be of more help :(

---

