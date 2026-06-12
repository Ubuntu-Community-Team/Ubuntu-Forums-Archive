---
title: "Google Calendar into Conky"
date: 2008-06-04
forum: Tutorials
---

### Post by pt123 on 2008-06-04
Here is a simple tutorial on getting your Google Calendar on Conky. 
Google calendar is a very useful due to it's accessibility, while Conky is great way to display information in subtle manner.

GCalcli is a command line tool that lets you access your Google Calendar in a terminal. 
[http://code.google.com/p/gcalcli/](http://code.google.com/p/gcalcli/)

Thankfully it was added to the repositories in Hardy.


**Step One GCalcli**
To install gcalcli
```
sudo apt-get install gcalcli
```

Then in your home folder you need to create a config file with your Google Calendar logins. Create the file by running this command:
```
gedit ~/.gcalclirc
```

Then in text file enter your Google Calendar username & password in this format. Note in the username in don't include the "@gmail.com" part. 

```

[gcalcli]
user: yourusername
pw: yourpassword

``` 

If you want to test it enter this command in a terminal
```
gcalcli --nc agenda
```

It should list an agenda from your calendar for the next five days

You need to create the script file below to update the file with your Google Calendar data.
In the script you need to set 1 variable, the file path to the text file that will hold the calendar data.


```

#!/bin/bash
gcalcli --nc agenda | tee /pathToTextFile/gcal.txt

```
Edit: This post explains how to get your agenda for the next 2 months
[http://ubuntuforums.org/showpost.php?p=6228269&postcount=45](http://ubuntuforums.org/showpost.php?p=6228269&postcount=45)

You need to cut and past the above code into a file called gcal.sh.
Then you can run the script in a terminal by
```
bash /pathtoFolder/gcal.sh
```

Note. Gcalcli provides many other outputs including a calendar like output. You can read about it here:
[http://code.google.com/p/gcalcli/wiki/HowTo](http://code.google.com/p/gcalcli/wiki/HowTo)

If you want you can get the script to run every X minutes by editing your cron. I don't want to go into this . This thread deals Cron comprehensively
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

**Step Two Conky**
To get the Google Calendar data in your Conky, edit your config file.
```
gedit .conkyrc 
```

Then find the word "TEXT" in it, below it you can add the following line
```
${head /pathToTextFile/gcal.txt 10 20}
```

Note. 10 is the number of lines from the top of text file. You also need to increase your text buffer if you planning to read many lines by editing the following lines. 
```

# Maximum size of buffer for user text, i.e. below TEXT line.default is 16384 bytes
max_user_text 32768

```


That's it. I have attached a small example of how it can look like.

This was tested on the Gcalci & Conky that came with Hardy 8.04

You can also find my Conky & Tomboy tutorial here:
[http://ubuntuforums.org/showthread.php?t=805211](http://ubuntuforums.org/showthread.php?t=805211)

---

### Post by sweetthdevil on 2008-06-08
Sounds great, I was actually wainting for that for a while, however I have an error running the "gcalcli --nc agenda" command. 

```
sweetth@ubuntu:~$ gcalcli --nc agenda
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1114, in <module>
    DoooooItHippieMonster()
  File "/usr/bin/gcalcli", line 1044, in DoooooItHippieMonster
    gcal.AgendaQuery()
  File "/usr/bin/gcalcli", line 777, in AgendaQuery
    eventList = self._SearchForCalEvents(start, end, start, None)
  File "/usr/bin/gcalcli", line 710, in _SearchForCalEvents
    feed = self.gcal.CalendarQuery(query)
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 115, in CalendarQuery
    result = self.Query(query.ToUri())
  File "/var/lib/python-support/python2.5/gdata/calendar/service.py", line 111, in Query
    result = self.Get(uri)
  File "/var/lib/python-support/python2.5/gdata/service.py", line 556, in Get
    'reason': server_response.reason, 'body': result_body}
gdata.service.RequestError: {'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}

```

---

### Post by pt123 on 2008-06-08
> **sweetthdevil said:**
> Sounds great, I was actually wainting for that for a while, however I have an error running the "gcalcli --nc agenda" command. 

```
sweetth@ubuntu:~$ gcalcli --nc agenda
gdata.service.RequestError: {'status': 400, 'body': 'Invalid UserId p', 'reason': 'Bad Request'}

```


The error is there you are placing the incorrect user id in the config file. 

When you place the username in the config file don't include the "@gmail.com" part.

---

### Post by sweetthdevil on 2008-06-08
Well actually no, the problem come from the weather calendar I was using witinh my Google calendar, I deleted it, and is now working fine.

Many thanks, great how to!

---

### Post by pt123 on 2008-06-08
> **sweetthdevil said:**
> 
Many thanks, great how to!

Why not use Thanks button ;) [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]

---

### Post by sweetthdevil on 2008-06-08
Done, funny, never knew what was the icon for... :lolflag:

---

### Post by inter-m on 2008-06-09
that sounds great and i would like to try it... but how would i do it on Gusty since its not available on its repos...

Khalaf

---

### Post by pt123 on 2008-06-11
> **inter-m said:**
> that sounds great and i would like to try it... but how would i do it on Gusty since its not available on its repos...

Khalaf

You can but it is a little meessy. When I was on hardy I had to install using the tar ball. There were problems with dependencies (if recall correctly python-xml-tree)

---

### Post by sweetthdevil on 2008-06-12
Hi me again... 

a quick question, I am looking for an option to go to the next line after a certain numbers of characters, trouble is the output of my scheddule is often too long, so i whish to cut the lenght by half, but if I use the "maximum_width" option it's just cut the text from one side. 

Do you know what I mean?

---

### Post by PinkFloyd102489 on 2008-06-12
I keep getting a "failed to authenticate". Im not doing the Conky thing, I just want to access the calendar from the command line.

---

### Post by sweetthdevil on 2008-06-12
are you sure you of your username and password? do not put user@gmail but only user.

---

### Post by sweetthdevil on 2008-06-13
Just to know, have you seen my previous question? 

> Hi me again...

a quick question, I am looking for an option to go to the next line after a certain numbers of characters, trouble is the output of my scheddule is often too long, so i whish to cut the lenght by half, but if I use the "maximum_width" option it's just cut the text from one side.

Do you know what I mean?

Thanks

---

### Post by pt123 on 2008-06-13
> **sweetthdevil said:**
> Just to know, have you seen my previous question? 
Thanks

Yeah word wrap is a problem with conky but you can use this script by Heiner Steven

[http://ubuntuforums.org/showpost.php?p=1907955&postcount=61](http://ubuntuforums.org/showpost.php?p=1907955&postcount=61)

save it in your script folder called wordwrap.sh

Then call the code in a bash script like this:
```

cat ~/journal/gcal.txt | ~/scripts/wordwrap.sh -w 46 -o 10 > ~/journal/gcalWW.txt

```

where 46 is word wrap characters. 
gcal.txt is where the original Google calendar is retrieved to.

---

### Post by sweetthdevil on 2008-06-14
Fantastic exaclty what I was looking for!!! Work perfectly!!!

Many thanks!!

---

### Post by Mandrake12 on 2008-06-14
Superb, great stuff! thanx!

---

### Post by Kronos2785 on 2008-06-21
> **pt123 said:**
> Yeah word wrap is a problem with conky but you can use this script by Heiner Steven

[http://ubuntuforums.org/showpost.php?p=1907955&postcount=61](http://ubuntuforums.org/showpost.php?p=1907955&postcount=61)

save it in your script folder called wordwrap.sh

Then call the code in a bash script like this:
```

cat ~/journal/gcal.txt | ~/scripts/wordwrap.sh -w 46 -o 10 > ~/journal/gcalWW.txt

```

where 46 is word wrap characters. 
gcal.txt is where the original Google calendar is retrieved to.

Unfortunately, that word wrap program removes the whitespace that keeps times and dates inline vertically. Does anyone know of another word wrap script (or have the skills to edit this one) so that whitespace is not removed during the wrapping procedure?

regards

---

### Post by sweetthdevil on 2008-06-21
could you show me what you mean with a screenshot?

---

### Post by sweetthdevil on 2008-06-21
could you please show me with a screenshot?

---

### Post by pt123 on 2008-06-21
> **Kronos2785 said:**
> Unfortunately, that word wrap program removes the whitespace that keeps times and dates inline vertically. Does anyone know of another word wrap script (or have the skills to edit this one) so that whitespace is not removed during the wrapping procedure?

regards

Yeah it doesn't , I remember when looking for this it was listed as a TODO by the original coder. 

You might want to search for a python word wrap script. 
e.g.
[http://iwiwdsmi.blogspot.com/2007/09/python-word-wrap-function.html](http://iwiwdsmi.blogspot.com/2007/09/python-word-wrap-function.html)

With Python it is a lot easier for someone new to edit the code.

Off-topic - while doing the search I just came across that even Aptana doesn't have a wordwrap function
[http://forums.aptana.com/viewtopic.php?t=3358](http://forums.aptana.com/viewtopic.php?t=3358)

---

### Post by kaivalagi on 2008-06-24
Hi All,

I don't mean to steal anyone's thunder, but I thought this was a good place to make mention my post, and get some feedback.

I have created a Google Calendar python script specifically for Conky, which uses the gdata api rather than the cli app talked about here. I've done this on the premise that it should be much more customizable than would otherwise be possible.

You can find the post here: [http://ubuntuforums.org/showthread.php?t=837385](http://ubuntuforums.org/showthread.php?t=837385)

I would appreciate some feedback on the script and any suggestions for further functionality are welcome.

Key feature are:
[LIST]
[*]Utilises the Google Calendar API.
[*]Supports the use of a template to define the layout of each event output
[*]Supports regional datetime formats, by way of system locales
[*]Optional event limit so you can reduce the total output in Conky if you have lot's of events, events should be returned earliest first (needs testing)
[/LIST]

I have already created a weather forecasting script for Conky in much the same manner, which has gone down well, and I hope the same can be the case for this one.

Cheers

---

### Post by Madwida on 2008-09-23
Hi 

I followed this guide and was successful until I got here: 

In the script you need to set 1 variable, the file path to the text file that will hold the calendar data.
Code:

#!/bin/bash
/usr/bin/gcalcli --nc agenda | tee /pathToTextFile/gcal.txt

You need to cut and past the above code into a file called gcal.sh.
Then you can run the script in a terminal by
Code:

sh /pathtoFolder/gcal.sh

I am really a nooby.  I created the file using gedit and changed the /pathToTextFile/ to /home.  But then I could not get it to work.  It kept saying .sh cannot open /home  

I know how to use Conky and have one running now.  My problem seems to hinge on my not understanding or performing properly the steps laid out above.  

Thanks for any help.

---

### Post by unutbu on 2008-09-23
Change /pathToTextFile/ to /home/USERNAME/
(where USERNAME is your username)

Make a directory called bin in your home account (/home/USERNAME/bin).

Save the script gcal.sh in /home/USERNAME/bin.

Use gedit to either create or edit ~/.profile. Put these lines in ~/.profile:
```

PATH=$PATH:$HOME/bin
export PATH

```
Save and exit gedit.
Log out. Log back in. This will make the change in PATH effective.
From now on, whenever you type a command, ~/bin will be among the directories searched to find the executable. Thus you can just type the name of the script without the entire path and the script will execute. 

Make the script executable:
```

chmod +x ~/bin/gcal.sh

```
Now to run the script simply type:
```

gcal.sh
```

---

### Post by pt123 on 2008-09-24
as mentioned above you need to use /home/username/gcal.txt

You also don't have to edit the ~./profile 
if you are running the script file in cron using "/home/username/gcal.sh"

---

### Post by Madwida on 2008-09-24
Hi again 

So, this is the output from the terminal: 

christian@christian-laptop:~$ gcalcli --nc agenda

Wed Sep 24  10:00am  Olin Music

Thu Sep 25  12:00am  4:15pm - 5 Maya Ballet

Fri Sep 26   8:30am  pt Olin
            12:00pm  Lunch with Guy Ortolano

Sat Sep 27   2:00pm  Maya Glass Palette

Mon Sep 29  12:00am  Rosh Hashana ends Oct 1

christian@christian-laptop:~$ sudo gedit .gcal.sh.
[sudo] password for christian: 
christian@christian-laptop:~$ sh /home/christian/gcal.sh
sh: Can't open /home/christian/gcal.sh
christian@christian-laptop:~$ 

I created the script file and then renamed the txt file and then entered the command into the terminal.  But what am I doing wrong?  It's probably ovbious to well seasoned users, but not me.  And I have no pride about this so point out the obvious!  Thanks

---

### Post by unutbu on 2008-09-24
Try this:
```

sudo chown $USER:$USER .gcal.sh. # Makes you (the normal user) owner of the script
mv .gcal.sh. gcal.sh             # Changes the name of the script to gcal.sh
chmod +x gcal.sh                 # Makes sure the script is executable
./gal.sh                         # Runs the script

```
Explanation:
When you run```

sudo gedit .gcal.sh.
```
you are creating a file called ".gcal.sh." as root. So the file becomes owned by root.
Also, the file should be called "gcal.sh", rather than ".gcal.sh."

---

### Post by Madwida on 2008-09-24
Thanks!  :guitar:

I think the problem was simply that I had added the . to the sh.  I read your instructions to include the ., but it turns out it was just a period.  

I have included a screenshot of it working.

---

### Post by pt123 on 2008-09-25
Good to hear

---

### Post by Madwida on 2008-09-25
> **unutbu said:**
> Try this:
```

sudo chown $USER:$USER .gcal.sh. # Makes you (the normal user) owner of the script
mv .gcal.sh. gcal.sh             # Changes the name of the script to gcal.sh
chmod +x gcal.sh                 # Makes sure the script is executable
./gal.sh                         # Runs the script

```
Explanation:
When you run```

sudo gedit .gcal.sh.
```
you are creating a file called ".gcal.sh." as root. So the file becomes owned by root.
Also, the file should be called "gcal.sh", rather than ".gcal.sh."


Hi again, 

I went to log on this evening and am locked in an infinite log in loop (right now I am in failsafe gnome).  Could it be that following the above somehow changed my user status?  If so, how do I undo the change?  If not, any ideas as to what might have happened--the only changes I have made to the system are the ones followed here.  

Many thanks

---

### Post by Madwida on 2008-09-25
And this is a message from syslog: 

Sep 25 19:14:26 christian-laptop gdm[6133]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

---

### Post by lilong10 on 2008-09-26
> **sweetthdevil said:**
> Well actually no, the problem come from the weather calendar I was using witinh my Google calendar, I deleted it, and is now working fine.

Many thanks, great how to!

I had the same problem too... The script worked fine after I deleted weather calendar. 

I wonder if that's because the weather calendar has a user id but no password?

---

### Post by pt123 on 2008-09-26
> **Madwida said:**
> And this is a message from syslog: 

Sep 25 19:14:26 christian-laptop gdm[6133]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

boot in recovery mode 

go into a terminal

cd /home
ls 

post output of ls here

if you find your user directory
cd yourusername

then 
ls -a

and see if you have folders inside

from this this thread
[http://ubuntuforums.org/showthread.php?t=140365](http://ubuntuforums.org/showthread.php?t=140365)

you might want to try and rename these files to some other name and reboot
~/.gnome2/session
~/.gnome2/session-manual

---

### Post by Madwida on 2008-09-26
> **pt123 said:**
> boot in recovery mode 

go into a terminal

cd /home
ls 

post output of ls here

if you find your user directory
cd yourusername

then 
ls -a

and see if you have folders inside


from this this thread
[http://ubuntuforums.org/showthread.php?t=140365](http://ubuntuforums.org/showthread.php?t=140365)

you might want to try and rename these files to some other name and reboot
~/.gnome2/session
~/.gnome2/session-manual

Thanks.  Here's the output.  I did not run it from recovery mode as I was able to log in after changing the desktop background (as suggested in another thread; I have no idea why that worked) while working in failsafe gnome.

Hope this helps:

christian@christian-laptop:~$ cd /home
christian@christian-laptop:/home$ ls
christian
christian@christian-laptop:/home$ ls -a
.  ..  christian
christian@christian-laptop:/home$ 
christian@christian-laptop:/home$

---

### Post by pt123 on 2008-09-26
you left out the step : 
cd yourusername
i.e
 cd christian

---

### Post by Madwida on 2008-09-27
> **pt123 said:**
> you left out the step : 
cd yourusername
i.e
 cd christian

Ooops.  Is this what you need? 

christian@christian-laptop:~$ cd /home
christian@christian-laptop:/home$ ls
christian
christian@christian-laptop:/home$ ls -a
.  ..  christian
christian@christian-laptop:/home$ 
christian@christian-laptop:/home$ cd /home
christian@christian-laptop:/home$ ls
christian
christian@christian-laptop:/home$ cd christian
christian@christian-laptop:~$ ls -a
.                                  .gnome2_private
..                                 .gnupg
.adobe                             .gstreamer-0.10
array-apt-key.asc                  .gtk-bookmarks
.bash_history                      .gvfs
.bash_logout                       .ICEauthority
.bashrc                            .icons
.cache                             Intuition.emerald
.compiz                            .local
.config                            .macromedia
.conkyrc                           madwifi-hal-0.10.5.6-r3835-20080801
.conkyrc~                          madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
.conky_start.sh                    .metacity
Desktop                            .mozilla
.dmrc                              .mozilla-thunderbird
Documents                          Music
eee-osd_2.1-0eeeXubuntu1_i386.deb  .nautilus
eeepc-linux                        .openoffice.org2
eeepc-linux-0.2.tar.gz             Pictures
.emerald                           .profile
.esd_auth                          Public
Examples                           .pulse
.fontconfig                        .pulse-cookie
.fr-VgHgzu                         .recently-used
.gcalclirc                         .recently-used.xbel
.gcal.sh                           RiceeeyTweak.sh
.gcal.sh~                          .screenlets
.gcal.sh.~                         .ssh
gcal.sh                            .sudo_as_admin_successful
gcal.sh~                           Templates
gcal.sh.                           .themes
gcal.sh.~                          .thumbnails
gcal.txt                           .update-manager-core
.gconf                             .update-notifier
.gconfd                            Videos
.gksu.lock                         .Xauthority
.gnome                             .xsession-errors
.gnome2
christian@christian-laptop:~$

---

### Post by pt123 on 2008-09-27
cd into .gnome2
and rename these two files and try rebooting
session
session-manual

so the instructions to do the above, after you have "cd usernamed"
cd .gnome2
mv session session_old
mv session-manual session-manual_old

---

### Post by Madwida on 2008-09-27
> **pt123 said:**
> cd into .gnome2
and rename these two files and try rebooting
session
session-manual

so the instructions to do the above, after you have "cd usernamed"
cd .gnome2
mv session session_old
mv session-manual session-manual_old

Hi again  

Am I missing something?  I just do not seem to able to get this!  Please see new output.  And again:  many thanks for the help

christian@christian-laptop:/home$ cd chrstian
bash: cd: chrstian: No such file or directory
christian@christian-laptop:/home$ cd christian
christian@christian-laptop:~$ cd .gnome2
[email]christian@christian-laptop:~/.gnom[/email]e2$ mv session_old
mv: missing destination file operand after `session_old'
Try `mv --help' for more information.
[email]christian@christian-laptop:~/.gnom[/email]e2$ mv session-manual session-manual_old
mv: cannot stat `session-manual': No such file or directory
[email]christian@christian-laptop:~/.gnom[/email]e2$

---

### Post by pt123 on 2008-09-27
> **Madwida said:**
> mv session_old


You need to see an optometrist. 

That is not why I wrote in my post.

---

### Post by Madwida on 2008-09-28
> **pt123 said:**
> You need to see an optometrist. 

That is not why I wrote in my post.

Perhaps you're joking around, but I am trying to follow your instructions, I am grateful for.  So, if I make a mistake, well, I guess it turns out I'm human

---

### Post by Madwida on 2008-09-28
> **Madwida said:**
> Perhaps you're joking around, but I am trying to follow your instructions, I am grateful for.  So, if I make a mistake, well, I guess it turns out I'm human

So, now my panel is missing.  I realize I did not properly follow your instructions, but now I'd like to get my panel back.  Is there some way to do this?  And, is possible, keep Google calendar in Conky as I really like it?

---

### Post by Madwida on 2008-09-28
> **Madwida said:**
> So, now my panel is missing.  I realize I did not properly follow your instructions, but now I'd like to get my panel back.  Is there some way to do this?  And, is possible, keep Google calendar in Conky as I really like it?

Hi 

Just a little more info: I went in via failsafe terminal; ran gnome-panel; then killall gnome-panel; then rebooted; then ran failsafe gnome and changed the desktop background (as suggested in another post).  I was then able to log, with Conky and your Google calendar script added, in after having changed the desktop background.  

But I wonder what happened and whether or not the steps you suggested above (which, yes, I mistakenly did not follow precisely) can be run again?  

Thanks from a noobie!

---

### Post by pt123 on 2008-09-29
> **Madwida said:**
> But I wonder what happened and whether or not the steps you suggested above (which, yes, I mistakenly did not follow precisely) can be run again?  
Why do you want to run them again if everything is back to normal?

If you lose the panel you can run this in the terminal it will install the default panels
sudo apt-get install --reinstall gnome-panel

---

### Post by AppleSteve on 2008-09-29
Nice tutorial, Google Calendar is quite a decent piece of software, got me out of trouble at the wekend, too :D, thanks.

---

### Post by Madwida on 2008-09-29
> **pt123 said:**
> Why do you want to run them again if everything is back to normal?

If you lose the panel you can run this in the terminal it will install the default panels
sudo apt-get install --reinstall gnome-panel

Hi 

I'd like to run them again b/c I have to repeat these steps each time I want to get back into my system.  I am still stuck in the infinite loop and my panel is still missing (yes, I will run the reinstall noted above).  But I would like to reset things back to where they were when I first installed Google cal into Conky.  I am too new at this to be able to simply go back and undo things.  Please help--thanks!

---

### Post by pt123 on 2008-09-30
you are combining steps from different how to's I have no clue where you are. 

You pretty much have to do a step by step with screenshots for anyone to know and see what you are seeing.

---

### Post by pt123 on 2008-11-22
small update the default agenda function only gets the next 5 days. Sometimes you might not have many items in those 5 days. 
So you might want to get the the list of items for the next 2 months. 
To do this follow this you can adjust you script to this:

```

#!/bin/bash
#figure out the dates
todaysDate=`date +"%m/%d/%Y"`
monthsAhead=`date --date='2 months' +"%m/%d/%Y"` 

gcalcli --nc agenda $todaysDate $monthsAhead 

```

---

### Post by Piraja on 2008-12-03
Hey, thanks for the tutorial!
 
I'm having some difficulties; when I try to launch Conky this is what I get:

```
Conky: head logfile does not exist, or you do not have correct permissions
```

I can assure you my permission are right. And if I remove the last line

[HTML]${head ~/.gcal/gcal.txt 10 20}[/HTML]

it works fine again, without Google Calendar, of course. I could access Google Calendar via Terminal, following your instructions, but could not integrate it into my custom .conkyrc. PFA my working .conkyrc as well as the modified version, with your lines added.

(You can see screenshots of my Conky in my other posts, e.g. [this]("http://ubuntuforums.org/showpost.php?p=6292492&postcount=53") stupid quuestion.)

---

### Post by pt123 on 2008-12-04
rather than using ~/.gcal..... 

try using /home/yourusername/.gcal....

---

### Post by Piraja on 2008-12-04
Thanks! That worked.

---

### Post by MikeBrown on 2009-02-02
Hey,
First off thanks for typing out this tutorial. It would really add to my conky if I could get it to work (I've probably made a mistake somewhere)

I can't get past the gcalcli --nc agenda terminal testing command. 

Here's my output: 
exeter@Vordhosbn:~$ gcalcli --nc agenda
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1114, in <module>
    DoooooItHippieMonster()
  File "/usr/bin/gcalcli", line 959, in DoooooItHippieMonster
    cfg = LoadConfig(configFile)
  File "/usr/bin/gcalcli", line 881, in LoadConfig
    config.read(os.path.expanduser(configFile))
  File "/usr/lib/python2.5/ConfigParser.py", line 267, in read
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/exeter/.gcalclirc, line: 1
'user: emmersonbrown\n'

I went onto my google calendar and noticed that I too had the weather calendar activated, so i removed it. I then did a killall of conky to reboot it (perhaps that may fix it): Nope. 

I followed your instructions exactly as they should've been 
The gcal.sh and gcal.txt files are in the path '/home/exeter/'

gcal.sh includes this command:
#!/bin/bash
gcalcli --nc agenda | tee /home/exeter/gcal.txt

gcal.txt is empty. Not sure if it's supposed to be. 

.gcalclirc is also in home/exeter/ and includes:
user: emmersonbrown
pw: [password in lower case] 

Any help that could be given would be greatly appreciated! 

Again, thanks for helping out, just wish I could figure out why it doesn't work for me!

---

### Post by MikeBrown on 2009-02-03
I don't know if it's that part that's causing the error as the gcalcli --agenda command in terminal isn't giving the schedule as it's supposed to, instead it's giving the dooitmonsterhippie nonsense...
I don't know why it's not giving the right output, but I think it's a configuration problem before i get to the other files.

---

### Post by pt123 on 2009-02-03
> **MikeBrown said:**
> Hey,
.gcalclirc is also in home/exeter/ and includes:
user: emmersonbrown
pw: [password in lower case] 


Do you have the this line at the top of your .gcalclirc 
```
[gcalcli]
```

---

### Post by MikeBrown on 2009-02-03
Yes. When I booted up today conky wouldn't even start...

I think I broke it...

***EDIT: Sorry, I'll be more specific. Conky will not launch and is giving me the same "Head Does Not Exist" error that another user was getting earlier in this thread. 
OUTPUT:
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right. [(I've been getting this error since I installed, 
I don't think it has to do with anything in this thread)]
Conky: can't parse X color '#FF6600T' 
Conky: head logfile does not exist, or you do not have correct permissions

I looked in my .conkyrc file to see if I was trying to pull from ~/.gcal but here's the line that was in there:  "  ${head /home/exter/gcal.txt 10 20}" So I don't think that's the case. If I remove the "${head...." line I pasted in the previous sentence, then Conky does still start up.

***EDIT #2: I realized that my ${head/.... line was missing an "e" as my login name is "exeter" not "exter".... gotta love those little mistakes that break the whole program lol. Now conky loads and it shows "Logfile empty" at the bottom of conky where my calendar would go. I don't know why I'm getting this error as there are things scheduled for today, tomorrow and next Tuesday. I assume the calendar has a 7 day outlook? Or is it 5?

---

### Post by pt123 on 2009-02-03
> **MikeBrown said:**
> 
***EDIT #2: I realized that my ${head/.... line was missing an "e" as my login name is "exeter" not "exter".... gotta love those little mistakes that break the whole program lol. Now conky loads and it shows "Logfile empty" at the bottom of conky where my calendar would go. I don't know why I'm getting this error as there are things scheduled for today, tomorrow and next Tuesday. I assume the calendar has a 7 day outlook? Or is it 5?

Logfile is empty it just means that there is not data. 

What happens when you run gcalcli in a terminal?

Also when you wrote password in lowercase, I am assuming you no uppercase letters in your password.

---

### Post by MikeBrown on 2009-02-04
exeter@Vordhosbn:~$ gcalcli
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1114, in <module>
    DoooooItHippieMonster()
  File "/usr/bin/gcalcli", line 959, in DoooooItHippieMonster
    cfg = LoadConfig(configFile)
  File "/usr/bin/gcalcli", line 881, in LoadConfig
    config.read(os.path.expanduser(configFile))
  File "/usr/lib/python2.5/ConfigParser.py", line 267, in read
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/exeter/.gcalclirc, line: 1
' [gcalcli]\n'

No, my password does not have any upper-case letters in it, meaning it's stored in the Google servers as 'cheeseburger' not CheeseBurger' or etc.

***EDIT: The script just started working. I don't know if I touched something, moved something around, sneezed on my computer wrong or what, but it's working now.... 

Thanks to the OP for this how-to, once the thanks button returns I will be sure to click it for ya! 

- Mike

---

### Post by pt123 on 2009-02-05
Good to hear

---

### Post by MikeBrown on 2009-02-09
Is there a command that I can enter into terminal to force the gcal to update? It doesn't seem to be doing so automatically. I've had one event showing up in calendar since it started working and when i do the gcalcli --nc agenda command in terminal it shows new events, it's just not writing to the gcal.txt

***EDIT: Nevermind, I went back and read the crontab entry. Plus the /sh /pathtofile/gcal.sh entry. 
Problem Solved!

---

### Post by Tohasj on 2009-02-15
I've tried to setup my Conky for reading my Google Calender, but I have a little problem. When I execute the gcal.sh manually everything is normal and my appointmens are visible in Conky. 

But I've setup my crontab to execute gcal.sh every half hour. That happens fine but only the first appointment is written to the gcal.txt file. And so also the first apointment is visible in Conky.

**My crontab file contains this rule: **

30 * * * * /etc/conky/scripts/gcal.sh

**After this bash is executed the gcal.txt file contains only this:**


Sun Feb 15   8:00pm  Indienen laatste studiemeting

Thu Feb 19

Can someone please help me?
Thanks in advance

---

### Post by pt123 on 2009-02-16
> **Tohasj said:**
> 
**My crontab file contains this rule: **

30 * * * * /etc/conky/scripts/gcal.sh

**After this bash is executed the gcal.txt file contains only this:**

Thanks in advance

Why are you running that script from /etc/conky folder wouldn't you need sudo permissions to execute it?

To get the script to run every 30 minutes cron needs to be like this:
*/30 * * * * /home/yourusername/scripts/gcal.sh

---

### Post by Tohasj on 2009-02-16
Thanks, I will try it out this evening

---

### Post by paranoidandroidz on 2009-04-02
By default, anyone know when the cron would update the gcal agenda if I didnt touch it. Im using Jaunty btw.

thanks

---

### Post by pt123 on 2009-04-02
not sure exactly what you mean, was it runnning (in Ibex)?

anyway you view your current cron by doing this
cat /etc/crontab

---

### Post by paranoidandroidz on 2009-04-03
sorry my misunderstanding, I didnt realise I had to update the crontab otherwise it wouldnt update. Its still all fairly new to me. The script updates it when I run it so hopefully

1 12 * * * /home/d/gcal.sh

means it will update at 12.01pm everyday. 

Great tutorial btw, cheers for your help as well

---

### Post by paranoidandroidz on 2009-04-03
ok that didnt work, and it wasnt jus because I missed the 0 in front.

When I run the script in terminal it updates my conky but it does come up with this message:

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

Any ideas?

---

### Post by pt123 on 2009-04-03
There seems to be a bug in Jaunty
[https://bugs.launchpad.net/subvertpy/+bug/323270](https://bugs.launchpad.net/subvertpy/+bug/323270)

it is a warning so it should still run fine,

I think your crontab is wrong can you check the tutorial I linked to in the original post

---

### Post by paranoidandroidz on 2009-04-03
hi thanks for your reply

If I look at cat /etc/crontab  then theres no jobs listed

But if I run crontab -l it shows the one I ve created. I even used your example from the previous page and still nothing. I dont get it.

Maybe theres a couple of bugs like you mention, I may have to revisit in a couple of weeks, Im sure I would have exerted less energy if I jus manually run the script every couple of days for the next 2 years....

I wish i'd stayed on 8.10 now, ushare stopped working with my xbox as well, but anyway thats for a different day 

Cheers for all your help

---

### Post by pt123 on 2009-04-03
> **paranoidandroidz said:**
> hi thanks for your reply

If I look at cat /etc/crontab  then theres no jobs listed

Does it have text like this 

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

```

> 
But if I run crontab -l it shows the one I ve created. I even used your example from the previous page and still nothing. I dont get it.

I added the following to get the script to run every minutes on Jaunty.
```
*/5 * * * * /home/myuserdir/scripts/gcalAgenda.sh
```
add it is running fine as the output text file has it's mod. date changed every five minutes. 

Do you have the script file set to executable? (as cron needs this)
```
su chmod +x /pathToScriptFile/gcal.sh 
```

> 
I wish i'd stayed on 8.10 now, 
So was this tutorial working on Ibex for you or is this the first time you are trying it?

---

### Post by paranoidandroidz on 2009-04-04
hi, thank you so much, its all working now, I copied your example of the every 5 minutes and it worked, I must have had a spelling mistake or sumthin, hours of fidlin and it was probably schoolboy, appreciate you spending the time.

Now, if only I can figure out how to get this in the middle of my screen.

---

### Post by pt123 on 2009-04-04
conky lets you set padding so you can align it to the left and place the padding to 40% times the width of your resolution

---

### Post by paranoidandroidz on 2009-04-04
many thanks, I shall look into it

---

### Post by gighsmighly on 2009-08-29
Hi!    I very much appreciate your coding efforts as it will greatly improve my productivity (once i get it working) during this semester..

my problem is:

[samuel@vii Stems]$ ./gcalcli calw

```
$ ./gcalcli calw

+----------+----------+----------+----------+----------+----------+----------+
|Sunday    |Monday    |Tuesday   |Wednesday |Thursday  |Friday    |Saturday  |
+----------+----------+----------+----------+----------+----------+----------+
|23 Aug    |24 Aug    |25 Aug    |26 Aug    |27 Aug    |28 Aug ***|29 Aug    |
Traceback (most recent call last):
  File "./gcalcli", line 1114, in <module>
    DoooooItHippieMonster()
  File "./gcalcli", line 1066, in DoooooItHippieMonster
    gcal.CalQuery(args[0])
  File "./gcalcli", line 819, in CalQuery
    self._GraphEvents(cmd, start, count, eventList)
  File "./gcalcli", line 543, in _GraphEvents
    eventList)
  File "./gcalcli", line 396, in _GetWeekEventStrings
    tmpTimeStr.strip() + " " + event.title.text.strip()
AttributeError: 'NoneType' object has no attribute 'strip'

```

wassap w/ dat?

i'm on fedora10 fluxbox

---

### Post by suurvey on 2009-08-29
i dunno

---

### Post by pt123 on 2009-08-29
> **gighsmighly said:**
> Hi!    I very much appreciate your coding efforts as it will greatly improve my productivity (once i get it working) during this semester..

my problem is:

[samuel@vii Stems]$ ./gcalcli calw

i'm on fedora10 fluxbox

it could be this :
fails at empty event description
[http://code.google.com/p/gcalcli/issues/detail?id=26](http://code.google.com/p/gcalcli/issues/detail?id=26)

---

### Post by Deguello on 2010-03-09
> **sweetthdevil said:**
> Well actually no, the problem come from the weather calendar I was using witinh my Google calendar, I deleted it, and is now working fine.

Many thanks, great how to!

I too was having a difficult time trying to figure out why I was having a problem and it boiled down to the weather calender within google calender...it was not good enough to uncheck it, but I had to actually unsubscribe to get the script to return anything....

---

### Post by hudebuntu on 2011-08-15
"You need to create the script file below to update the file with your Google Calendar data.
In the script you need to set 1 variable, the file path to the text file that will hold the calendar data."



Code:
#!/bin/bash
gcalcli --nc agenda | tee /pathToTextFile/gcal.txt

[B]Hi, I am new to ubuntu and I dont really know how to accomplish these steps above. Can someone explain me in details?? :confused:

Thanks a lot
[/B]

---

### Post by hudebuntu on 2011-11-18
meanwhile i found a site which explains it really simply how to use google calender with conky:

[http://ubuntuguide.net/display-google-calendar-on-ubuntu-desktop-using-conky](http://ubuntuguide.net/display-google-calendar-on-ubuntu-desktop-using-conky)


But now it shows me just 2 weeks and not four...how can i configure that???? (first it was ok but now one half of  my conky calender is cut off)

---

### Post by pt123 on 2011-11-19
you need to increase the size of the conky window, post a screenshot

---

### Post by wpwend42 on 2012-05-06
Okay I am trying to install this, but I get to this point...
[I]
n the script you need to set 1 variable, the file path to the text file that will hold the calendar data.


Code:
#!/bin/bash
gcalcli --nc agenda | tee /pathToTextFile/gcal.txt
Edit: This post explains how to get your agenda for the next 2 months
[http://ubuntuforums.org/showpost.php...9&postcount=45](http://ubuntuforums.org/showpost.php...9&postcount=45)

You need to cut and past the above code into a file called gcal.sh.[/I]

Two things...

[LIST]
[*]How do I create gcal.sh.?
[*]Where does it go?
[/LIST]

---

### Post by pt123 on 2012-05-06
wherever you keep your script files
eg. /home/your_username/scripts/gcal.sh

to create it 
gedit /home/your_username/scripts/gcal.sh

---

### Post by wpwend42 on 2012-06-16
Thank you this worked really well!

---

### Post by pt123 on 2012-06-16
that's nice to hear

---

### Post by wpwend42 on 2012-06-17
Okay, hopefully final question...

If I wanted the GCAL to update in Conky every 30 minutes, what do I add to the Cron file?

---

### Post by pt123 on 2012-06-17
> **wpwend42 said:**
> 
If I wanted the GCAL to update in Conky every 30 minutes, what do I add to the Cron file?

In stall an application called Gnome Schedule, it will be a GUI to cron. 

Then add a task like this:

---

### Post by wpwend42 on 2012-06-17
Okay...when I try to test it, I get "permission denied" as an output in the terminal.

---

### Post by pt123 on 2012-06-17
where do you keep your script file and what permissions do  you have on that file

---

### Post by wpwend42 on 2012-06-17
/myusername/Scripts/gcal.sh

Everything is set to permission to read and write...

---

### Post by pt123 on 2012-06-17
change /myusername to ~/ like in my example

---

### Post by wpwend42 on 2012-06-17
I got it to work! I didn't make the file executable before. It works now.

---

### Post by wpwend42 on 2012-07-08
This works well, but only shows the first X tasks on my calendar each day. What do I change to make it show more?

---

### Post by pt123 on 2012-07-08
can you give an example of all the tasks it should be showing

---

### Post by wpwend42 on 2012-07-08
Erm, I meant events on my calendar. I always think of them as tasks. Sorry!


Say I have 15 events on my calendar. What do I change to get them all to display in Conky? Right now it only shows up to about 2pm and that isn't really helping.

Is there a way to make it update to the moment, or can it only display from midnight on?

---

### Post by pt123 on 2012-07-08
change the 10 (for 10 lines) to something greater like 20 or 30
in the script file
```

cat ~/journal/cal.txt | ~/scripts/wordwrap.sh -w 46 -o **10**  | sed 's/12:00am//g' | sed ':a;N;$!ba;s/\n\n/\n/g' > ~/journal/gcalWW.txt

```


**sorry do this as the above is for word wrap**
in the conky rc file change the 10 to 30 
${head /pathToTextFile/gcal.txt 10 20}

---

### Post by wpwend42 on 2012-07-08
Ah, perfect. I figured it was that number, but didn't want to tinker until I was sure.

---

### Post by GrouchyGaijin on 2012-07-14
Hi Guys,

I have a question.

How can I change the agenda option to show a list of all events for a full month and not just five days.  I don't want a graphical calendar print out in Conky just a list for the whole month.

I found the answer
```
${color6}Google Calendar Agenda July 1 - Aug 31, 2012${color}${font}
${execi 300 gcalcli --nc --cal='xxxxx' agenda '07/01/2012' '08/31/2012'}
```

---

### Post by wpwend42 on 2012-08-18
Is there a way to get this to work in two factor authentication turned on?

---

### Post by pt123 on 2012-08-18
what to hide the .google credentials file?

---

### Post by wpwend42 on 2012-08-18
No, just if I generally have two factor authentication turned on in my google account. Since I turned it on earlier today, my GCal in Conky won't load.

---

### Post by pt123 on 2012-08-18
check/ask the gcalcli homepage

[https://github.com/insanum/gcalcli](https://github.com/insanum/gcalcli)

---

### Post by wpwend42 on 2012-08-18
It looks like, from what I can see, there isn't a variable for adding the token (like you would user name, password, etc).

---

### Post by sbjaved on 2013-04-03
running gcalcli with --https param causes it to crash:

```
saad@beast:~$ gcalcli --https calm
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1524, in <module>
    BowChickaWowWow()
  File "/usr/bin/gcalcli", line 1426, in BowChickaWowWow
    borderColor=borderColor)
  File "/usr/bin/gcalcli", line 378, in __init__
    cal.gcalcli_username   = urllib.unquote(match.group(1))
AttributeError: 'NoneType' object has no attribute 'group'

```
Runs fine w/o --https though.

---

### Post by GrouchyGaijin on 2013-04-03
I'm running version 2.3 and that bug is fixed in my version.
I see on github there is now a version 3.1
[https://github.com/insanum/gcalcli](https://github.com/insanum/gcalcli)

---

### Post by sbjaved on 2013-04-03
I switched to the git version as well which implements oauth2 so u dont even a need a .gcalclirc

---

### Post by Jacoobic on 2013-05-08
Hi there, i'm kinda new here, so if this post is in a bad section, i'm sorry for that :)
So, i tried to use conky for viewing my google calendar, using a .conkyrc file as follows /found that one in a how-to somewhere/:

alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
double_buffer yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 8096
 
TEXT
${execi 300 gcalcli --nc --cals=owner calw 4}

but when i run conky from terminal, the output looks like this:```
[COLOR=#222222][FONT=Verdana]jakub@jakub-AO531h ~ $ conky[/FONT][/COLOR]Conky: desktop window (e00029) is subwindow of root window (ab)
Conky: window type - override
Conky: drawing to created window (0x3000001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1524, in <module>
    BowChickaWowWow()
  File "/usr/bin/gcalcli", line 1469, in BowChickaWowWow
    gcal.CalQuery(args[0], count=int(args[1]))
  File "/usr/bin/gcalcli", line 1011, in CalQuery
    self._GraphEvents(cmd, start, count, eventList)
  File "/usr/bin/gcalcli", line 712, in _GraphEvents
    PrintMsg(CLR_NRM(), line + "\n")
  File "/usr/bin/gcalcli", line 239, in PrintMsg
    sys.stdout.write(unicode(msg, 'UTF-8'))
TypeError: decoding Unicode is not supported



```
I've read many websites about this, yet still haven't found a solution, if i delete the .conkyrc file, conky works /then it looks like in an enclosed screenshot/.
Thanks for any help :)
J.

[ATTACH=CONFIG]242320[/ATTACH]

---

### Post by GrouchyGaijin on 2013-05-08
Does gcalcli work correctly in the terminal?  What version of gcalcli are you running?

---

### Post by Jacoobic on 2013-05-08
yes, gcalcli works correctly.....i'm using version 2.1, obtained via apt-get

---

### Post by GrouchyGaijin on 2013-05-08
Hmmm then it seems the problem is that Conky can't handle the unicode text.
I know there is a command specifically to set Conky to display unicode.
The man to ask about this is Sector_11.  He hangs out on the Post your Conky Screenshot Thread here:[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

On another note, does the version you are using have the bug that causes a crash when trying to access Goolge via ssl?
You should probably switch to the latest version from GitHub.  See my signature for a link.

---

### Post by Jacoobic on 2013-05-08
thank you, i will ask there as well......also, i have found the 2.4 on github, but i'm not sure about how to install it, could you help me a bit?

---

### Post by GrouchyGaijin on 2013-05-08
Sure - I'm in class now, but can write some instructions this evening.

---

### Post by Jacoobic on 2013-05-08
great, thank you :)

---

