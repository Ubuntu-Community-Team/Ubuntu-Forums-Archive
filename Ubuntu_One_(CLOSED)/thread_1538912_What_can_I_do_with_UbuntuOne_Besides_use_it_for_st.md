---
title: "What can I do with UbuntuOne? Besides use it for storage?"
date: 2010-07-25
forum: Ubuntu One (CLOSED)
---

### Post by Nick_Jinn on 2010-07-25
What are some cool tricks and things you can use Ubuntu One for? Are there apps and stuff you can use from it besides sharing music? Can I use it to sync sticky notes or calendars even when both people are not online at the same time? Can you use it for limited web hosting?

---

### Post by grahammechanical on 2010-07-27
You can mark files as "Publish file."  This attaches a URL to the file. You can see the URL when you click on More. Give someone this URL and if they direct their web browser to that address they can either open or download the file. I am doing this with PDF documents that can be read on any computer if they have a PDF viewer installed. It seems to be standard nowadays. I created a PDf with the URLs on it. Sent it to a friend in Russia. And he is able to open or download the files that I have set to publish even though he is not using Linux and does not have Ubuntu One installed. I think that this is better than emailing the files to him. It is a form of selective on-line publishing. 

Regards.

---

### Post by duanedesign on 2010-07-30
Here is a blog post I have been working on about just this topic.
**Interesting uses for Ubuntu One**
Ubuntu One is a great program/service with many uses, some obvious some not so obvious. Here are a few creative uses for Ubuntu One that some people have come up with.

**Create Your Own Browser Start Page**
You can create a custom Start Page for all your computers using the Ubuntu One publish feature that makes files accesible through a URL. You can create a page with your bookmarks, RSS feeds, or whatever HTML-fu you can pull off. To do this, create the HTML file and put it in your Ubuntu One folder or a UDF (User Designated Folder). Then right-click on the file and select 'Publish via Ubuntu One'. After that right-click and select 'Copy Public URL'. You can do this through Nautilus or from the WebUI, the latter being a little quicker. From there it is only a matter of dropping the URL in your favorite browsers preferencces.

**Dont wait until you get Home to Download that Torrent**
Download a torrent to your computer while you are away. You will want to set up your torrent client to monitor a folder. In Transmission it is Edit > Preferences > Torrents 'Automatically add torrents from...'. Then you will set that folder to sync with Ubuntu One. Ubuntu One can sync any folder in the users $HOME by r-clicking on the folder and selecting 'Syncronize with Ubuntu One'. Then when you are away from home you just need to add the torrent to the folder using the WebUI.

**Monitor your Desktop**
Keep track of your computer while you are away. Want to see the progress of a task you left running or catch unauthorized users? Set up a cronjob to take a picture of your desktop every so often and save it in your Ubuntu One Folder or other UDF(User Designated Folder). To do this, open a terminal window and enter  'sudo crontab -e'  without the quotes. An editor will open and you will add a line that looks similar to this (with your username of course):

01 04 * * * import -window root -quality 100 "/home/duanedesign/Ubuntu\ One/screenshots/$(date +"%m-%l-%M").png"

This example saves a picture in the users Ubuntu One directory in a folder named screenshots. The 5 numbers at the beginning are in the following format:

minute(0-59), hour(0-23, 0 = midnight), day(1-31), month(1-12), weekday(0-6, 0 = Sunday)

So my example takes a picture of the desktop at 4:01. Since I didn't specify a month or day it will execute everyday.
Another example:
15 14 1 * *
This will run at 2:15pm on the first of every month.
Save your changes and your new crontab will be installed. Exiting without saving will leave your crontab untouched.

**NOTE:** I have not gotten this cron job to work yet. If anyone has any input please post it.

---

### Post by ehabh on 2010-07-30
Nice creative ways, duanedesign, on a more simple note, i use ubuntu one mostly for the tomboy notes sync. Once you use tomboy you get hooked and with one you can get your fix even when you are not on your ubuntu.

---

### Post by Nick_Jinn on 2010-07-30
Can you install apps to Ubuntu one?

I have an Android tablet when I am out and about, besides my Ubuntu laptop. When using android can I run a torrent program from UbuntuOne?

I think there is an app called transdroid or something.....or am I thinking of something else. I guess you can use a non local torrent application running on a different PC then access those files remotely? I don't know how to do that and I don't know much about setting up ports or proxies. Its on my to do list.

It would be cool if I could access my Ubuntu

---

