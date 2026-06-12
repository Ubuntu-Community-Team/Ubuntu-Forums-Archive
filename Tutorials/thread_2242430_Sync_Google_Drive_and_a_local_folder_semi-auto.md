---
title: "Sync Google Drive and a local folder semi-auto"
date: 2014-09-01
forum: Tutorials
---

### Post by wd5gnr2 on 2014-09-01
I had tried using a fuse file system that mounts your Google drive (the ocaml solution) but honestly it was very slow and took a long time to do things like do an ls of the top level. 

Grive allows you to sync with no issue, but you have to manually run it -- it isn't automated. Until now.

Step 1: Install grive

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install grive

```
There are some other ppa's out there. This is the one I used. The original project is on github: [https://github.com/Grive/grive](https://github.com/Grive/grive)

You'll need to run grive with the -a option once to authorize it to your Google account.

Pick a directory to make your "Google drive" for example ~/gdrive. For this example I will assume the full path is
/home/USER/gdrive.

Step 2: Install incron
You may already have it

```
sudo apt-get install incron

```

Step 3: Get the script
I have a script called grive-incron you can download from github [https://raw.githubusercontent.com/wd5gnr/grive/master/scripts/grive-incron](https://raw.githubusercontent.com/wd5gnr/grive/master/scripts/grive-incron)

Put it somewhere executable (e.g., /usr/local/bin) and make it executable:

```

sudo cp grive-incron /usr/local/bin
sudo chmod +x /usr/local/bin/grive-incron

```

Step 4: Set up incron
From a shell as your usual user run incrontab -e:

```

incrontab -e

```
This will start an editor. If you already have things in there, don't disturb them. Just add this to the end:
```

/home/USER/gdrive IN_CREATE,IN_DELETE,IN_CLOSE_WRITE,IN_MOVE /usr/local/bin/grive-incron $# /home/USER/gdrive\


```

Save and exit the editor.

At this point, any changes you make to your ~/gdrive directory will get sent up to Google Drive. It takes a few minutes and if you want to see if it is working try:
```

ps alx | grep grive

```

You should see grive running for a minute or two after you make a change. There may be more than one copy of grive-incron and that's ok.

Step 5: Periodic Updates
So far this is a one way street. You will add a cron script to update your local folder periodically. You can check out the man page for cron to see your options but this line will update at 5 and 35 minutes after the hour:

```

5,35 * * * * /usr/bin/grive -p /home/USER/gdrive

```


Run the following command:
```

crontab -e

```

An editor will pop up again. Don't disturb any existing lines, just add the line above to the end.

Step 6: Enjoy
Now when you make changes to ~/gdrive they will push up to the Google drive. Every 30 minutes, any changes you make in the cloud will appear on your machine. If you want to force the issue just run:
```

grive -p /home/USER/gdrive

```

Just be sure to patch all the /USER/ references and/or any other directory names you've changed.

---

