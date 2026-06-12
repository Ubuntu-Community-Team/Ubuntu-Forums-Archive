---
title: "How often does it check for changes?"
date: 2010-06-06
forum: Ubuntu One (CLOSED)
---

### Post by flyver on 2010-06-06
I've been searching around for this, but couldn't find the answer.

1- How often does it check for changes?
2- Does it "see" changes in an .odt document?
3- Does it choose not to upload the file again if it hasn't changed since last time?
4- I have added files from the Ubuntu One website. Will it update the file if it changes, or will it only check the Ubuntu One folder in my home folder?
5- If I copy a file from say my music folder to the Ubuntu One folder, will Ubuntu One know that it has to check the music folder for changes?

As you can see, I have absolutely no knowledge about syncronisation.

Thanks!

---

### Post by zekopeko on 2010-06-06
> **flyver said:**
> I've been searching around for this, but couldn't find the answer.

1- How often does it check for changes?
2- Does it "see" changes in an .odt document?
3- Does it choose not to upload the file again if it hasn't changed since last time?
4- I have added files from the Ubuntu One website. Will it update the file if it changes, or will it only check the Ubuntu One folder in my home folder?
5- If I copy a file from say my music folder to the Ubuntu One folder, will Ubuntu One know that it has to check the music folder for changes?

As you can see, I have absolutely no knowledge about syncronisation.

Thanks!

1. It should check every time a file changes. More about it in 2.

2. U1 doesn't know that you are editing a file in Openoffice until you save the file. Lets say you edit a file in Openoffice. You save the file. The file gets a timestamp that it was changed. U1 gets notified by the system that the file has been modified by looking at that timestamp. U1 syncs the file.

3. It shouldn't upload files that haven't changed and are already on U1 servers.

4. Any change you make to the files on the U1 website should get downloaded to every computer that is connected to U1. The opposite also applies. Any change you make to a file on ANY computer gets synced to U1 servers and then to other computers.

5. U1 only monitors folders that you said it should. By default the is the Ubuntu One folder which is always synced. To get some other folder that isn't inside the Ubuntu One folder to sync, lets says Documents, simply right click on it and select the Syncronize with Ubuntu One option from the menu. I have this option in Ubuntu 10.04.

For more information you can go here: [https://wiki.ubuntu.com/UbuntuOne/FAQ](https://wiki.ubuntu.com/UbuntuOne/FAQ)

---

