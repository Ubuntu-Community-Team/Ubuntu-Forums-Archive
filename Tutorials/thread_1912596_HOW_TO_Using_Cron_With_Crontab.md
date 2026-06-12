---
title: "HOW TO: Using Cron With Crontab"
date: 2012-01-20
forum: Tutorials
---

### Post by trikster_x on 2012-01-20
[SIZE="4"]_[COLOR="Red"]A Bit of Information About Cron_:[/COLOR][/SIZE] 

Cron is a CLI(Command Line Interface) program that runs in the background and executes jobs(commands or scripts) that are stored in a crontab file, which is used to specify what time a job should run. Each user has the ability to create a crontab file, whose jobs will be run regardless of the user being logged in. In addition their is a single "sudo" crontab file that has the ability to run ROOT level jobs without the need for password verification. Once every minute cron wakes up, checks all crontab files and runs any commands that are associated with that time. It can be very useful for running backup scripts or automating your updates, among other things.

[COLOR="Red"][SIZE="4"]_Setting Up A Crontab File_:[/SIZE][/COLOR]

[SIZE="3"][COLOR="SeaGreen"]Running Crontab:[/COLOR][/SIZE]
To use cron, you must first run the following command in a terminal:
```
crontab -e
```

If you wish to make a job that would require administrative priviliges(i.e. you have to use sudo to run the script or command) then you should use:
```
sudo crontab -e
```

If it is your first time running crontab on your system, you will be asked to choose a CLI text editor to make the default editor every time you open a crontab. The editor you choose does not make a large difference, since creating a crontab is not a complex operation. Once you have chosen an editor, you will be taken to your crontab entry screen. You will notice a lot of text with [COLOR="Green"]**#**[/COLOR] at the beginning of each line. The text is a simple overview of how to make a job. A [COLOR="Green"]**#**[/COLOR] comments out a line of text, so cron ignores it.

_[SIZE="3"][COLOR="Red"]Creating a Job:[/SIZE][/COLOR]_
A simple job consists of six parts. The first five are the **[COLOR="Green"][B]time descriptor**[/COLOR][/b]. These parts tell cron when the job should be run. The sixth part is for the [COLOR="Green"]**command or script**[/COLOR]. Let's go over the time descriptor first.

[SIZE="3"][COLOR="SeaGreen"]Describing Time:[/COLOR][/SIZE]
The layout for the time descriptor is:
```
Minute[0-59, *] Hour[0(midnight)-23, *] DayOfMonth[1-31, *] MonthOfYear[1-12, *] DayOfWeek[0(sunday)-6, *]
```

An asterisk in any part of the time descriptor means the job will run on every occurence of that time period. As an example, if we want to run a command at 5:30 am on the 15th day of every month we would use the following time descriptor:
```
30 5 15 * *
```

Notice the asterisks in the place of the month and day of the week portions of the time descriptor. Those indicate that the job will run every month on any day of the week. If you wish to run a job at multiple times, there are a couple operators we can use. Seperating numbers by a [COLOR="Green"]**comma**[/COLOR]([COLOR="Green"]**,**[/COLOR]) with no space will cause the job to run at all of the specified times:
```
0,30 5 1 * *
```

In this example descriptor the job will run at 5:00 am and 5:30 am on the first of every month.

If you want the job to run on every instance of a time period for a specific amount of time, you can use a [COLOR="Green"]**hyphen**[/COLOR]([COLOR="Green"]**-**[/COLOR]) with no spaces:
```
30 5 1-15 * *
```

This descriptor runs the job at 5:30 am on the first **through** the 15th of every month.

A time period can be divided by using including a [COLOR="Green"]**slash**[/COLOR]([COLOR="Green"]**/**[/COLOR]) with a number to divide the time period by:
```
*/10 5 15 * *
```

This will run the job on any minute that can be divided by 10, with 0 always being the first instance of the job, regardless of divisor. Keep in mind the script will only be run on numbers in the time period that can be divided [COLOR="Blue"]**EVENLY**[/COLOR] as described. [COLOR="Blue"]**So a minute descriptor of */7 will run every seven minutes starting at 0. This means the job will run at minute 56, then again at 0 if it runs every hour of the day.**[/COLOR]

There are a few special strings you can put in place of the entire time descriptor segment:
[LIST=1]
[*]@reboot = Run once, at startup.
[*]@yearly = Run once a year, "0 0 1 1 *".
[*]@annually = (same as @yearly)
[*]@monthly = Run once a month, "0 0 1 * *".
[*]@weekly = Run once a week, "0 0 * * 0".
[*]@daily = Run once a day, "0 0 * * *".
[*]@midnight = (same as @daily)
[*]@hourly =Run once an hour, "0 * * * *".
[/LIST]

[SIZE="3"][COLOR="SeaGreen"]Giving Cron Something To Do:[/COLOR][/SIZE]
Now that you know how to tell cron WHEN to run, you need to be able to tell cron WHAT to run. The first thing we want to do is make sure cron knows what paths it can expect to find a command in. Add the following to crontab, [COLOR="Blue"]**preferably as the very first line**[/COLOR]:
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```

Now you can enter commands as you normally would in a terminal. Let's use a simple one that is easy to see the results of:
```
mkdir /home/USERNAME/crontest
```

Before we use it in crontab, let's see what to expect from the command. [COLOR="Blue"]**Open a terminal window and type the command, using you username in the appropriate spot, then press enter**[/COLOR]. You will notice this created an empty directory named [COLOR="Green"]**crontest**[/COLOR] in your home folder. Once you are satisfied the command works, delete the newly created directory and open your crontab. Input the following line in the first blank line of crontab, changing the minutes and hour to something a couple minutes ahead of local time, and again changing the USERNAME:
```
45 5 * * * mkdir /home/USERNAME/crontest
```

Once the time you entered comes around, check your home directory again and you will see the file "crontest" has been created again, this time without you doing anything. Congratulations, you have created your first cronjob! Now open crontab again and delete the job, or it will continue running every day at the specified time.

Crontab can also be used to run a script, as long as it has been set as executable. To do that, simply put the path of the script in place of the command.

[COLOR="Blue"]**Note: Sometimes cron refuses to play nice with PATH. If you absolutely can't get a command to run, you may need to input the full path in the job itself. To get the full path of a command, use the following command in a terminal:**[/COLOR]
```
which *commandname*
```

Just switch **[COLOR="Green"]commandname[/COLOR]** with your command. For the case of our example crontab entry, the command would look like this with the full path:
```
/bin/mkdir /home/USERNAME/crontest
```

[SIZE="4"][COLOR="Red"]_Advanced Usage_:[/COLOR][/SIZE]

[SIZE="3"][COLOR="SeaGreen"]Outputting to a Log File:[/COLOR][/SIZE]
Sometimes it is beneficial to send some information to a log file to keep track of whether or not a command ran, and what it did when it ran. Let's consider an example using our earlier crontab entry:
```
45 5 * * * mkdir /home/USERNAME/crontest && echo "directory created" >> /home/USERNAME/Documents/test.log
```

Now when this job runs it will create a file called test.log in the specified user's Documents directory. The file will contain the words [COLOR="Green"]**directory created**[/COLOR] as indicated by the echo command. In this case, the [COLOR="Green"]**>>**[/COLOR] between the command and log file path indicates the log will not be overwritten with any subsequent log entries, it will simply have any new text appended to the bottom of the list. If you wish to have the file overwritten every time the job is run, simply use one [COLOR="Green"]**>**[/COLOR]. 

This syntax will only send the [COLOR="Green"]**standard output**[/COLOR](text from the echo command) to the log, ignoring any [COLOR="Green"]**standard errors**[/COLOR]. [COLOR="Green"]**If we wish to include the standard errors with the standard output**[/COLOR], we simply add [COLOR="Green"]**2>&1**[/COLOR] after the log file path:

```
45 5 * * * mkdir /home/USERNAME/crontest && echo "directory created" >> /home/USERNAME/Documents/test.log 2>&1
```

Now if the command encounters any errors when it attempts to run, these will be written to the log file as well.

[COLOR="SeaGreen"][SIZE="3"]Running A GUI Program:[/SIZE][/COLOR]
[COLOR="Blue"]**Running a GUI based program through cron requires we tell cron which desktop and monitor we want the program to be run on**[/COLOR]. There are a few methods to do this. For a single monitor setup, or if you don't want to have to specify the monitor to run on in every job you can use this method:
```
XAUTHORITY=~/.Xauthority
DISPLAY=:0.0
```

Simply place that bit of code on a line above all the jobs in the crontab. Keep in mind, this will run all programs on the same monitor, so it is not well suited for systems with mulitple monitors. In that case you can use the following as part of the job itself:
```
env DISPLAY=:0.0
```

[COLOR="Green"]**Following is an example in crontab format with an explanation of what it means**[/COLOR]:
```
0 6 * * * env DISPLAY=:0.0 banshee --play
```  

The above job opens the Banshee music player and begin playback at 6 am every day. [COLOR="Blue"]**The first number specifies the desktop the program will be run on(0 = current desktop), the second number specifies the monitor/screen to be run on(0 = first monitor/screen)**[/COLOR]. You can also use the [COLOR="Green"]**export**[/COLOR] command, though the syntax is a bit different. You will need to include A set of [COLOR="Green"]**double ampersand**[/COLOR]([COLOR="Green"]**&&**[/COLOR]) to make this method work:

```
0 6 * * * export DISPLAY=:0.0 && banshee --play
```

[COLOR="Blue"]**It has been reported that for some users, none of the above methods will work through cron**[/COLOR]. In that event, simply make a script that contains the [COLOR="Green"]**env**[/COLOR] or [COLOR="Green"]**export**[/COLOR] commands along with whatever command you are trying to run it with. Using our banshee example, the script would look like this:
```
#!/bin/bash

env DISPLAY=:0.0
banshee --play
```

[COLOR="Blue"]**To make the script, simply copy/paste the example in an empty text file and name it alarm.sh or something similar**[/COLOR]. The [COLOR="Green"]**env**[/COLOR] and [COLOR="Green"]**export**[/COLOR] commands can be substituted for each other without any other modification to the script. While not completely necessary, it is suggested that you give all shell scripts a [COLOR="Green"]**.sh**[/COLOR] extension to make them more easily identifiable. Then you simply make the script executable by right clicking the file, opening the properties menu, going to the permissions tab, and checking the executable box. Once that is done, you can add the script as a job:
```
0 6 * * * /path/to/alarm.sh
```

It will run exactly the same as before.



I got most of the information for this guide at the [[COLOR="DarkOrchid"]Ubuntu Official Cron How-To[/COLOR]]("https://help.ubuntu.com/community/CronHowto").
This has also been a nice little go-to article for me:
[[COLOR="DarkOrchid"]http://adminschoice.com/crontab-quick-reference[/COLOR]]("http://adminschoice.com/crontab-quick-reference")
And finally, a site with a list of bash commands and a short description of their function:
[[COLOR="DarkOrchid"]http://ss64.com/bash/[/COLOR]]("http://ss64.com/bash/")

---

