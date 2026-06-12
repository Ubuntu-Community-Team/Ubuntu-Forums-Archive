---
title: "Feature request for USPcalrem"
date: 2007-01-12
forum: Ubuntu System Panel
---

### Post by ardchoille42 on 2007-01-12
I am using usp .41 on Ubuntu Dapper with USPcalrem .5

I have been using USPcalendar and USPremind and have noticed that when I click a future date in USPcalendar, the tasks and appointments for that day don't appear in USPreminder. I just assumed that these two plugins are "talking to each other". I noticed that in USPcalrem that when I click a future date, the tasks/appointments area appears (which makes my menu "jump") and shows the correct stuff for that day.. seems this plugin updates due to it being a single plugin.

My request is either:

1) Make is so that the USPcalendar and USPremind plugins can talk to each other,

or

2) Make it so that USPcalrem shows the tasks/appointments area all the time so the menu doesn't jump when I click on a date that has appointments..

Oh yeah, and an option to "go home", or shows today's date, in both plugins would be a benefit as well.

Are these things possible?

---

### Post by Malac on 2007-01-15
> **ardchoille42 said:**
> I am using usp .41 on Ubuntu Dapper with USPcalrem .5

I have been using USPcalendar and USPremind and have noticed that when I click a future date in USPcalendar, the tasks and appointments for that day don't appear in USPreminder. I just assumed that these two plugins are "talking to each other". I noticed that in USPcalrem that when I click a future date, the tasks/appointments area appears (which makes my menu "jump") and shows the correct stuff for that day.. seems this plugin updates due to it being a single plugin.

My request is either:

1) Make is so that the USPcalendar and USPremind plugins can talk to each other,

or

2) Make it so that USPcalrem shows the tasks/appointments area all the time so the menu doesn't jump when I click on a date that has appointments..

Oh yeah, and an option to "go home", or shows today's date, in both plugins would be a benefit as well.

Are these things possible?
Sorry for the delay in responding.

For Question 1).
USPremind was just for people who wanted to know what they had on today when they switched on their computer. It was never intended to copy the "full" calrem functionality. Whilst it is possible for the two plugins to communicate, for reasons connected with usp's code structure, it would make usp run rather slow and hog your system.
I would suggest using USPcalrem as detailed below.
For Question 2).
_Easy Solution._
Set height of calrem plugin to allow for Task/Appointments even if they're not there.
_Less Easy Solution_
```
gedit /home/*[COLOR=Gray]<yourusername>[/COLOR]*/.usp/plugins/USPcalrem.py
```and find this section at the bottom.
```
    if self.showtasksappoints != 0:
        if len(taskview)==0:
            self.wTree.get_widget("vbox2").hide()
        else:
            self.wTree.get_widget("vbox2").show()
        if len(appsview)==0:
            self.wTree.get_widget("vbox3").hide()
        else:
            self.wTree.get_widget("vbox3").show()
    else:
        self.wTree.get_widget("vbox2").hide()
        self.wTree.get_widget("vbox3").hide()
    return True
```and change it to :
```
    if self.showtasksappoints != 0:
        self.wTree.get_widget("vbox2").show()
        self.wTree.get_widget("vbox3").show()
    else:
        self.wTree.get_widget("vbox2").hide()
        self.wTree.get_widget("vbox3").hide()
    return True
```I will think about a way to get the return to today function in asap.
In the mean time double-clicking on the date will take you to today.
Hope this helps.

---

### Post by ardchoille42 on 2007-01-15
That does indeed help, thank you very much. I am learning python and your "less easy" solution was quite easy to implement and it worked perfectly.
I also found that if I change:

```

	if self.showtasksappoints != 0:
		self.wTree.get_widget("vbox2").show()

```

to

```

	if self.showtasksappoints != 0:
		self.wTree.get_widget("vbox2").hide()

```

and adjust the size of height_appoints in gconf-editor, then I don't get the scrollbars - which makes it look much better. I don't use the "Tasks" item in Evolution anyway so it doesn't matter if it doesn't appear in USP.

---

