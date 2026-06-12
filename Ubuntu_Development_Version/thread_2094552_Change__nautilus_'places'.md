---
title: "Change  nautilus 'places'"
date: 2012-12-14
forum: Ubuntu Development Version
---

### Post by ubername on 2012-12-14
Hi

Is it possible to change the entries in the 'places section in nautilus side bar? I never use Documents, Downloads, Music, Pictures or video, but there are plenty of other places I would like to have there (which I have in bookmarks, but that's right at the bottom). The options to Remove or Rename them on the right-click context menu are greyed out.

---

### Post by dino99 on 2012-12-14
right clicking on Applications to edit the Menu (alacarte) let you tweaks menu/submenus as you like.

---

### Post by philinux on 2012-12-14
> **ubername said:**
> Hi

Is it possible to change the entries in the 'places section in nautilus side bar? I never use Documents, Downloads, Music, Pictures or video, but there are plenty of other places I would like to have there (which I have in bookmarks, but that's right at the bottom). The options to Remove or Rename them on the right-click context menu are greyed out.

Not sure if there's a raring version yet. But ubuntu tweak can edit quicklists.

But in nautilus itself those were hardcoded. [http://askubuntu.com/questions/223665/is-it-possible-to-reorder-my-places-in-nautilus](http://askubuntu.com/questions/223665/is-it-possible-to-reorder-my-places-in-nautilus)

I'm booting into raring shortly will investigate further.

---

### Post by serdotlinecho on 2012-12-14
Atm, you cannot edit and add anything from here, right?

[IMG]http://i.imgur.com/L6eQl.png[/IMG]

---

### Post by ubername on 2012-12-14
> **serdotlinecho said:**
> Atm, you cannot edit and add anything from here, right?

[IMG]http://i.imgur.com/L6eQl.png[/IMG]
 
I don't know how to get that 'bookmarks' window! Any clues?

Edit: OK Found it. I've removed the entries I don't want, but they still appear in 'places' (and never appeared in 'bookmarks')

---

### Post by philinux on 2012-12-14
> **ubername said:**
> I don't know how to get that 'bookmarks' window! Any clues?

Click on Home Folder top left. There's a drop down.

---

### Post by ubername on 2012-12-14
> **philinux said:**
> Click on Home Folder top left. There's a drop down.

Cross post!

---

### Post by serdotlinecho on 2012-12-14
Or open and access Bookmarks window from HUD, tap Alt and type book, Enter.

[IMG]http://i.imgur.com/JS6BU.png[/IMG]

I don't like this vertical gnome-shell dropdown menu ](*,) Can we get back our normal horizontal unity appmenu?

> Edit: OK Found it. I've removed the entries I don't want, but they still appear in 'places' (and never appeared in 'bookmarks')

There is no + button to add new bookmarks. Can you change the location/path like /home/username/Documents to something else and rename the Bookmarks?

[IMG]http://i.imgur.com/l1ZJC.png[/IMG]

---

### Post by rrnbtter on 2012-12-14
Greetings,
The final product will be in April. No telling what it will be like. For myself, I don't like the missing "New File" option, but I'm pretty sure it will show at some point.  I think nautilus is still in development.  There will be some things that don't get added until the last day before the final release. 
Just my opinion. 
rrnbtter

---

### Post by serdotlinecho on 2012-12-14
> For myself, I don't like the missing "New File" option...

No...that "create new files" it's not missing...they want you to be "clever" ;)

[IMG]http://i.imgur.com/kBz7m.png[/IMG]

---

### Post by rrnbtter on 2012-12-14
Greetings,

Original by serdotlinecho
> No...that "create new files" it's not missing...they want you to be "clever" 

Thanks, Just went to the templates folder and copied over a text file and renamed it to "New Document"  and cleared it's contents. That fixed it. Thanks
rrnbtter

---

### Post by serdotlinecho on 2012-12-15
Nemo file manager looks and feel so much better!

[http://www.webupd8.org/2012/12/how-to-install-nemo-file-manager-in.html#more]("http://www.webupd8.org/2012/12/how-to-install-nemo-file-manager-in.html#more")

Well, ppa is available for 13.04

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable]("https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable")

---

### Post by Orange Kingdom on 2012-12-15
No Nemo standalone?

---

### Post by ubername on 2012-12-15
I think the product is now called 'files' FWIW. Just noticed in the 'About files' menu item, but the executable is still called nautilus.

Obviously still pretty beta. If you rename the target of one of the places items (which you can't remove) you get an error message. I will raise a bug.

---

### Post by mc4man on 2012-12-15
As mentioned you can't **add** to "Places" without source code changes.

5 of the built-in places can be removed from Places (Documents, Downloads, Music, Pictures, Videos 
The obvious easy way would be to delete those folders

If inclined one can keep all 5 folders as is & remove them from Places with some localized user-dir* files (3 I believe
screen shows none of them  in Places though all 5 still exist 
But myself don't see the point here

You can however turn any or all of the existing 5 into 'new folders', either with the same name symlinked to a new/different folder or just a new name altogether for the existing one
screen 2 ex. of renaming Pictures to Stuff, linking Documents to stuff

---

### Post by el_gallo_azul on 2013-10-25
> **dino99 said:**
> right clicking on Applications to edit the Menu (alacarte) 

What does this mean?

What do you mean by "Applications"?

Where?

I'm in the process of moving all my **/home/(user)** folders to my hard drive (to get it out of my solid-state drive), and discovered that Nautilus 'Places' hasn't started pointing to the new **/home/(user)** folders. That's a shame, because I expected it to.

---

### Post by cariboo on 2013-10-25
dino99 hasn't been back since the forum was hacked, but alacarte (Menu Editor) isn't used any more. If you put your home directory on a separate partition, you have to mount it in order to access it. If it isn't on a separate partition, [this Ask Ubuntu thread]("http://askubuntu.com/questions/21321/move-home-folder-to-second-drive") may help you solve your problem.

---

