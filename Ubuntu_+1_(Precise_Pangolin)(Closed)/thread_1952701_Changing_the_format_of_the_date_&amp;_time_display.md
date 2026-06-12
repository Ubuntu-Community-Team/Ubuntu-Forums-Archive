---
title: "Changing the format of the date &amp; time displayed in top panel?"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Trapper on 2012-04-04
U12.04 Unity

In 10.04 I could adjust the display format of the clock via gconf-editor and using **strftime syntax.**[FONT=Verdana] [/FONT]How can I go about doing the same in 12.04 unity?

---

### Post by cariboo on 2012-04-04
Click on the clock and select Time & Date Settings, then click the clock tab.

---

### Post by Trapper on 2012-04-04
> **cariboo907 said:**
> Click on the clock and select Time & Date Settings, then click the clock tab.

That's for the normal settings. I am speaking of things such as putting an extra space between the day and month, a comma after the calendar day, etc.

"Somewhere" there's a configurable file that controls what the clock in the panel actually displays and it's in this "sort of" format: %a%m%d%H%M

In Gnome 2 custom clock configuration could be done via edits to the clock applet using gconf-editor. I am just trying to figure out how it can be done in Unity.

---

### Post by kaldor on 2012-04-04
That would be a regional setting. Go to System Settings > Language Support > Regional Formats. 

Mine says "Wed 4 Apr 23:35"

---

### Post by Trapper on 2012-04-04
> **kaldor said:**
> That would be a regional setting. Go to System Settings > Language Support > Regional Formats. 

Mine says "Wed 4 Apr 23:35"

I'm not finding anything there that's allowing me to customize the display of (English) United States time.

With choices allowed, my clock displays               Wed Apr 4 10:25:43PM

I am wanting to display it as                                 Wed  Apr 4, 10:25:43 PM

It's only a matter of a couple of specifically positioned spaces and a comma. There's got to be a file somewhere that I can hack and insert those items.

---

### Post by jbicha on 2012-04-04
And for completion's sake (although I recommend you try Regional Formats first!):

In dconf-editor, you can set com.canonical.indicator.datetime time-format to custom and change the custom-time-format.

---

### Post by scradock on 2012-04-04
That allows you to choose another "standard set", but not to choose your own preferences.

Interestingly, the "Installed Files" list for Indicator-datetime" includes the file

/usr/share/applications/indicator-datetime-preferences.desktop

 which is not actually present in the stated location.

I'm guessing that would be the place to set personal preferences - can anyone confirm? And what would its contents be?

---

### Post by jbicha on 2012-04-04
That file is installed here. Open it up and see what the Exec line says...

---

### Post by scradock on 2012-04-04
Very strange: it is there in another Precise install - 479 bytes, the Exec line says "Exec=gnome-control-center indicator-datetime"

But in the install I was in when I first looked, it's just not there. Until - I saw a file labelled "Time & Date". Even in List View in Nautilus, that's what it's called. Only when I open a terminal and do "ls -la" do I see that it is indeed called "indicator-datetime-preferences.desktop".

I'm sorry, but this sort of thing really makes me mad! I went "off" Windows many years ago when M$ started doing crazy tricks like this - inventing "names" for files that were not in fact what the files were called, or listing files as if they were in one folder when they were in fact in another place entirely. Now we've got to deal with the same thing in Ubuntu? I don't think this is progress. Like many others in these forums, I enjoy being able to "tweak" my OS in so many ways, and this just makes it harder than it needs to be. /rant

---

### Post by mc4man on 2012-04-05
> **scradock said:**
> 
But in the install I was in when I first looked, it's just not there. Until - I saw a file labelled "Time & Date". Even in List View in Nautilus, that's what it's called. Only when I open a terminal and do "ls -la" do I see that it is indeed called "indicator-datetime-preferences.desktop".

I'm sorry, but this sort of thing really ...

There is nothing 'not right' there, that is the nature of .desktop files

There is the 'actual' file name - <whatever>.desktop, & the 'display' name which is determined by the Name= line in the .desktop 
( Name= can be whatever one wishes & freely edited if desired

---

### Post by stinkeye on 2012-04-05
Show your current settings
```
gsettings get com.canonical.indicator.datetime time-format
```
```
gsettings get com.canonical.indicator.datetime custom-time-format
```


Change to custom format...(shows as in pic)
```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format "[COLOR="Magenta"]%a %b %e, %l:%M %p[/COLOR]"
``` 
[COLOR="magenta"]Your format[/COLOR] ...put in extra spaces if gaps aren't big enough.


Back to default 
```
gsettings reset com.canonical.indicator.datetime time-format && gsettings reset com.canonical.indicator.datetime custom-time-format
```


For formats...
```
date --help
```

---

### Post by Trapper on 2012-04-05
> **jbicha said:**
> And for completion's sake (although I recommend you try Regional Formats first!):

In dconf-editor, you can set com.canonical.indicator.datetime time-format to custom and change the custom-time-format.


Regional Formats doesn't help because that's what is not customizable in the gui. However I did do the dconf-editor (after installing dconf-tools) routine below:

```

dconf-editor

com/canonical/indicator/datetime

Values=

custom-time-format  %a  %b %e, %l:%M:%S %p
locations ['UTC']
show-calendar checked
show-clock checked
time-format custom

All other boxes unchecked

Result = Thu  Apr 5, 11:48:07 AM

```

This gives me what I am wanting.

Now I see there are numerous other posts showing different ways to accomplish this. I will sort through them a try things to see how they work.

Thanks for your help. Actually, thank _all_ of you for your help and suggestions.

---

### Post by scradock on 2012-04-06
> **mc4man said:**
> There is nothing 'not right' there, that is the nature of .desktop files

There is the 'actual' file name - <whatever>.desktop, & the 'display' name which is determined by the Name= line in the .desktop 
( Name= can be whatever one wishes & freely edited if desired

Well, I see all that. What I'm unhappy with is roughly as follows:

the "Name=" line in the .desktop file is fine so that the System Settings application gives meaningful and pithy labels for the various control setting programs that it displays. 

BUT: nautilus is a file-handling program, and should surely display the true filename, not the label. Nautilus is not there to serve as an alternative to System Settings; it's there to enable me to find a file that someone has kindly told me the name of, or a list that I can select a likely item from.

Does that make sense?

---

### Post by jbicha on 2012-04-06
.desktops are shortcut files. The equivalent on Windows are .lnk files but Windows Explorer doesn't show the .lnk part.

---

### Post by stinkeye on 2012-04-06
> **scradock said:**
> 

Does that make sense?

No.

---

### Post by scradock on 2012-04-06
> **jbicha said:**
> .desktops are shortcut files. The equivalent on Windows are .lnk files but Windows Explorer doesn't show the .lnk part.
I guess that's why the behavior I ran into reminded me of Windows...

I really don't think it is the business of a File Manager to mimic the reactions of the application the file is related to. It's to declare what the file name and other attributes are. Windows got it wrong when Windows Explorer started showing _what the .lnk file linked to_ instead of the file name. I'm unhappy to find Ubuntu doing the same in Nautilus.

That's all.

---

### Post by jbicha on 2012-04-06
I think you definitely have the minority opinion.

Remember that Nautilus (or Windows Explorer) also takes care of the icons on the desktop. Desktop shortcuts should be named for what they're pointing to. Typical users don't care about how it works, and cluttering it up with names like Recycle Bin.lnk don't help.

The .desktop specification is pretty complex and it allows frontends to show either a long name or a short name for instance; there's far more information in the file than just the filename. It's more than just a link, it's a descriptive shortcut with an icon.

Even if it were a bug, it's a bug against Nautilus, not Ubuntu in particular.

---

### Post by scradock on 2012-04-07
OK, I guess you're right. It's a Nautilus bug, and I'm certainly not going to try disturbing the upstream folk with my antiquated preferences.

Thanks for responding, Jeremy - it's good to feel that there's someone there who can disagree on rational grounds!

---

### Post by dcstar on 2012-04-07
> **jbicha said:**
> 
......
In **dconf-editor**, you can set com.canonical.indicator.datetime time-format to custom and change the custom-time-format.

At last, the thing that can be used to change this crippled Gnome 3 environment back to what was easily done in Gnome 2.

---

### Post by Trapper on 2012-04-07
>  					Originally Posted by **jbicha** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11818509#post11818509") 				
 				[I]......
In **dconf-editor**, you can set com.canonical.indicator.datetime time-format to custom and change the custom-time-format.[/I]


> **dcstar said:**
> At last, the thing that can be used to change this crippled Gnome 3 environment back to what was easily done in Gnome 2.

Yup.

---

