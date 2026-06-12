---
title: "Security Updates and Daily Backups (Dapper)"
date: 2007-03-28
forum: Server Platforms
---

### Post by jnovek on 2007-03-28
Hello!

I am a long time linux user, but I am running my first Linux "server" that is not fully insulated from the internet by NAT.  I am pretty familiar with Linux and Unix in general, but I've never been very focused on stuff like security since I've always been more of a "linux on the desktop" guy.

This is just a small private CVS server for me and some frnieds to work on some "spare time" projects on.

I installed Dapper server, and poked around a bit.  It's pretty impressive, pleasantly uncomplicated compared to my Edgy desktop.  I'm only stuck on a few little things (I know that the problems below can be solved with an afternoon of scripting, but I thought there might be a more sophisticated way of doing them):

1) How can I do *JUST* security updates without commenting out all the other repos in my sources.list?  For bonus points, is there an easy way that I can set up a cron job that will check for security updates and E-Mail me if there are any available?

2) I would like the system to do daily backups of a few key things, i.e. CVS snapshots.  My "evil" plan was to throw a DVD+RW in the drive and have it burn any changes every night.  Nothing too fancy.  I don't trust the hardware on this system at all... Hard drives from the "old hard drives that are too small" box in the basement, old case and power supply that I had lying around, that kind of stuff.  Anyway, is there nice backup tool that can make this sort of stuff easy?

Thanks!

Jason

---

### Post by motin on 2007-03-28
1) Dunno exactly, but setting up a MTA together with a mail-alias for your user on the server running cron will result in that the output of the cron-job will be mailed to you. The cron job should be as simple as (as root) "apt-get update && apt-get upgrade -dVq" should do it. 

2) You probably will want to use a cron-job running rsync that mirrors your local directories with for example an ftp-server. Rsync will do incremental backups and always transfer the differences only between every mirror-session. 

You should definitely look into Subversion, btw - so much more flexible.

---

### Post by Brazen on 2007-03-28
I would look into cronapt, rather than creating your own cron script.

---

### Post by jnovek on 2007-03-29
Thanks!

I've been poking around for a few cron-apt examples... the docs are a bit sparse.  It looks like it will work well.

I was not clear above on how I want to do my backup procedure, probably because I wrote DVD+RW when I meant DVD+R.  I want to do nightlly backups, burning JUST the changes from the day before in significant places... i.e. changes in /etc, new nightly CVS snapshots, etc.  That way I'll have a record of our daily progress on the code and if I manage to bork the server I'll be able to look back and see what configs I've changed... and possibly roll back to a de-borked state.  Why?  Because I know deep down in my heart that if I CAN break something, I WILL break it.

Regarding SVN vs. CVS, I will try out SVN one of these days, but we're playing with a lot of technology that is new to us in this project, so I'm going to stick with CVS (which we're all familiar with).  Thanks for the heads up, though.

Jason

---

### Post by huygens on 2007-03-29
For the security update:
I have written a small article on how to create a script and define the crontab to [notify by e-mail of new security updates]("http://www.berthon.eu/ice_and_fire/?p=40"). As I do have only the main and restricted repository activated, and only edgy-security. I do receive only security updates.
It would need to be tweak a bit to accommodate checking only the security updates out of all possible updates (in case you have more repositories activated).
I have wrote the article based on two Ubuntu Wiki articles. They are both referenced in the above link.

To install only the security update, you could use aptitude instead of apt-get and use the flag '--target-release' with the value dapper-security (if you are using Ubuntu 6.06 LTS a.k.a. Dapper Drake). You could use this wiki article then: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

By mixing both articles, you could have the automatic security installation with the notification by e-mail :-)

---

### Post by huygens on 2007-03-29
I just found this article on back-up for the Server Edition :-) : [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Backup_Ubuntu_System](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Backup_Ubuntu_System)
I hope this can help!

---

### Post by maynardp on 2007-05-26
I use the following script (for now) to send notification messages regarding available package upgrades (can be limited to security as well)).  This produces very detailed output about the packages including depandacies and package descriptions.  This is definely more  info than I want - but it will work until I can write a script to provide the exact details I want....

NOTES:  
     apt-cache show <pkg>...  will detail both the installed package and available update.
     apt-cache rdepends <pkg> will detail packages that depend upon this package
        - I use this on my productions servers before I consider installaing package upgrades
        - try apt-cache rdepends libc6 if you want an idea of a dependancy tree

run from root crontab or use sudo from the command line

apt-get -qq -s upgrade |grep "^Inst" | grep security |awk '{ print $2 }'|xargs -I STDIN -n 1 sh -c 'echo -e "\n\n\n**************************\n" ; apt-cache show STDIN'

Command breakdown:
---------
apt-get -qq -s upgrade
 - simulates an upgrade and reports any packages that can be upgraded

grep "^Inst"
 - limits output from apt-get to just lines starting with "Inst"
 - yes this means in reality you can omit the '-qq' option from apt-get but it makes grep do more work

OPTIONAL grep security
 - further filter the output so that only Installation lines from 'security' sources will be displayed
 - personally - I don't use this part - but you were looking for security info

awk '{ print $2 }'
 - further filter apt-get output so that only the second column of output is displayed
 - this is the package name and it will be used in the next part of the command

xargs -I STDIN -n 1
 - xargs will read information from standard input (the awk output) and use it to make new commands
 - xargs works great for commands that do not take input from standard input
 - the -I STDIN options means replace STDIN with input from standard input
      - STDIN is just the string name I use, you can use whatever you like
 - the '-n 1' option means that create a new command for each value passed as standard input

sh -c
 - this means we are going to have 'xargs' run a shell and have the shell run the commands passed in quotes
 - this was done because I want 2 commands run not just one

'echo -e "\n\n\n**************************\n" ; apt-cache show STDIN'
 - this is the actual commands that are run
 - the first command is an echo statement used to put a separator between packages
 - ; (semi-colon) is a command separator
 - the second command uses apt-cache to show package details
 - STDIN is replaced with the names of packages output in the 'awk' command

If you  don't need the package separator in your output - this is a much simpler version

apt-get -qq -s upgrade |grep "^Inst" | grep security |awk '{ print $2 }'|xargs apt-cache show

But when you get 4 or more updates on the same day - this becomes difficult to read without the separator.


Pete

---

