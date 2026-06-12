---
title: "nautilus - partition names lost in left panel"
date: 2024-09-08
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-09-08
nautilus 1:47
In the old version of nautilus with 'Other Locations' I used to see the list of partitions in physical order with the label and the partition name. Now I only see the label and I don't have the partition name.
[https://askubuntu.com/questions/1526005/nautilus-47-partition-names-lost-in-left-panel](https://askubuntu.com/questions/1526005/nautilus-47-partition-names-lost-in-left-panel)

---

### Post by grahammechanical on 2024-09-08
You are getting more than I am. I do not see Other Locations any more. I cannot use Files 47.Beta.1 to access the other partitions. Two of the partitions appear in the dock, But the partition that is auto-mounted does not appear in the dock. So, I cannot access any directories under Computer. The Root directories.

Regards

---

### Post by corradoventu on 2024-09-08
In Nautilus 47 'Other Locations' is disappeared. to access directories under 'Cpmputer' you may use a trick as suggested in   [https://gitlab.gnome.org/GNOME/nautilus/-/issues/3537](https://gitlab.gnome.org/GNOME/nautilus/-/issues/3537)
You can access the root of your filesystem by simple typing / and Enter or Ctrl+l and navigating to their directory directly
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2076979)

---

### Post by grahammechanical on 2024-09-08
So, this is intentional by the Gnomes of Gnome and not up for discussion. Typical. 

I have got into the habit of using Files to find documents and videos stored on a Data partition that is auto mounted which then loads in the respective application. The alternative is to first load the application and then search for the document or video. A Person gets used to a certain way of working. 

I do know how to access the Data partition using the command line but I do not understand this:

> f you need / in the sidebar then you can go there and bookmark it from the pathbar menu.

Regards

---

### Post by 1fallen on 2024-09-08
Just out of curiosity, will "[COLOR=#F3F5F7][FONT=ui-monospace]gnome-disk-utility[/FONT][/COLOR]" see them?

---

### Post by grahammechanical on 2024-09-08
I think I have worked it out.

Open Files and click on the magnifying glass icon. The panel that appears will say Search Everywhere. Click on the button Search Settings. Now click Add Location and from the list of folders and locations select / or the folder that you most often want to go to in the Data partition such as /mnt/Data. Click Select.

Now open Files and click on the search panel and Home will change to the location = /home/username. Click the forward arrow and there we are - at Ubuntu (what used to be called Computer). And there is the mnt folder and inside it the Data folder. And inside that are the folders on my Data partition.

And they call this improvement. I suppose this improvement to Files makes sense if a person is of the opinion that the user is more likely to break the OS rather than sloppy programming. It has a point.

Regards

P.S. If I open Files and type in the search panel /mnt/Data   it opens in the Data partition.

---

### Post by jbicha on 2024-09-09
You can also drag a folder to the left sidebar to add it to your bookmarks. They reduced the number of hard-coded items in the sidebar because there were complaints.

---

