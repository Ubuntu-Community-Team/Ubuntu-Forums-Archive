---
title: "OneDrive directory"
date: 2019-03-13
forum: Ubuntu/Debian BASED
---

### Post by roweder on 2019-03-13
I have been using Elementary OS for about a week now.  I have installed onedrive using [these instructions]("https://github.com/skilion/onedrive"), and I have made my windows OneDrive directory suitable for use in linux by following [these directions (answer by vangarde with 0 upvotes)]("https://unix.stackexchange.com/questions/404159/accessing-onedrive-folder-on-windows-partition").  I am curious if it is possible to get Windows and Linux to use the same OneDrive directory?  

First of all, I don't know how to move the Linux OneDrive directory,[SUP]1[/SUP] and every time I try to find a solution my search results are drowned out by windows solutions.  I don't seem to be able to find instructions for moving the onedrive directory on Linux.  

Secondly, I don't know if putting the OneDrive directory in the same place for two operating systems would cause any issues when switching between one or the other.[SUP]2[/SUP]  Could it cause one to re-download the entire folder at startup each time?  Would the two OS's use different hidden files in the directories and end up creating duplicates upon duplicates every time I switch between operating systems?

And finally, the drive I have my OneDrive folder in is a Intel RST RAID 1 Mirror.  I can finally use the mirror correctly, as I just installed mdadm.  Would I need to set a command to run at startup that would mount that drive,[SUP]3[/SUP] before the OneDrive app tries to sync to it?  Also do startup commands actually get run in the order they are in in the startup applications list?  Or do they all start at the same time?

Would a command mounting drives refer to them as terms like sda and sdb or nvma and nvmb?[SUP]4[/SUP]   I have seen drives addressed that way on many occasions when I've used parted magic, but I haven't seen that notation too much in Elementary OS.  

This isn't urgent, I'd love to hear any discussion about this.  My onedrive has only 12gb of files in it.  The drive Elementary OS is installed on is 256gb, so it has plenty of room, it's just that the drive Windows syncs Onedrive to is an 8TB mirror (2 8TB drives).  

Thanks for any advice in advance!

---

### Post by wildmanne39 on 2019-03-13
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by jdeca57 on 2019-03-14
On Ubuntu 18.10 it is simple:
```
sudo apt install onedrive
```

and then run the command onedrive in a terminal.

It produces a strange url and you have to copy and paste it in a browser and then you are asked for login information. Provide it and consent to transfer of data. Only then you are directed to a blank page with an url. Copy that url and paste it as an answer in the data terminal where the onedrive command is running.

Syncing follows immediately.

To have an automatic syncing of the folder do the following:

systemctl --user enable onedrive 
systemctl --user start onedrive

There are actually no problems with sda or C: because onedrive syncs to a folder. And hidden files depending on the OS? That's an interesting question but I presume that it only copies data. LibreOffice opens Word data, pdf, jpeg, mp3 is readable so there are little problems sharing files.

And another point: of course only the data in the folder count. You can put 12 GB on a 10 TB drive and still it is only the 12 GB that are synced.

So the answer to the question can I share between Windows and Linux is simple: yes.

---

### Post by roweder on 2019-03-18
> **jdeca57 said:**
> On Ubuntu 18.10 it is simple:
```
sudo apt install onedrive
```
Does that work on 18.04?

I successfully got onedrive installed and syncing already, so my question is not about that.  Do you know how to move the onedrive directory?  And I'm not sure you got the specifics of my question.  I have windows and linux on two separate drives, and a third drive has my windows onedrive folder.  I'm asking if it is ok to have windows and linux both syncing to the exact same directory on that third drive (not at the same time).  

I am thinking of doing this mostly because the drive linux is installed on is small, and my onedrive size is going to grow.

---

### Post by roweder on 2019-03-18
> **wildmanne39 said:**
> *Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*
Why was this moved to a seemingly very quiet sub-sub-sub forum?  It is a relevant question for anyone on Ubuntu, elementary os juno is ubuntu 18.04.  The question pertains much more to onedrive useage and functionality than elementary os.

---

### Post by QIII on 2019-03-18
Because Elementary is NOT Ubuntu, but an independent OS based on Ubuntu.

The Ubuntu Forums exist to provide peer support for those who use one of the official flavors of Ubuntu.  As a courtesy, we also provide areas for other OSes such as Elementary and even Windows.

Whenever a new post is made in this thread, it will rise to the top of the activity stream and everyone will see it.  If you ever go more than about 12 hours without a response, simply add a new post with just the word "bump" and you'll go back to the top of the pile.

---

### Post by jdeca57 on 2019-03-18
> **roweder said:**
> Does that work on 18.04?

I successfully got onedrive installed and syncing already, so my question is not about that.  Do you know how to move the onedrive directory?  And I'm not sure you got the specifics of my question.  I have windows and linux on two separate drives, and a third drive has my windows onedrive folder.  I'm asking if it is ok to have windows and linux both syncing to the exact same directory on that third drive (not at the same time).  

I am thinking of doing this mostly because the drive linux is installed on is small, and my onedrive size is going to grow.

Again, I'm working on Ubuntu 18.10 and I can but suppose this works for you. On my system I have an hidden directory ~/.config/onedrive and a file ~/.config/onedrive/config and in that configuration file you can define the place of that onedrive directory. My situation is that I share data from different computers in the cloud and on a drive that's formatted for the OS on each computer. If you share the same drive with Windows and use ntfs you have to take into account that Windows can end in hibernation with unclean file systems so that it may be only read-only from the Linux side. But if Windows ends clean it should be possible to share with write access. I have no practical experience of that situation however.

---

