---
title: "UI- looking for X feature for Y file"
date: 2008-01-05
forum: Ubuntu Brainstorm
---

### Post by Mr.mouse on 2008-01-05
the idea is to help the user to find specific application\feature for a specific file, not depended on if the application is installed or not installed.

1. a. the user click right click on a file (on nautilus) then select "open with".
    b. or the user click right click on a file (on nautilus) then select: properties>"open with">add
    c. or the user download a file from firefox then select "Open with, Other"

2. the user get a UI with a list of application that can work with this file.
     this list contain:
     a. installed application like today on nautilus (right click on a file, properties>open with>add )
     b. recommend uninstalled application that can work with this file

under the list the user will see features information about the application (what can I do with this application)

- every format file need to have a different recommend application list
- the features list of all the application need to include most possible features that the user can do with a specific format file.

3. after the user select application\feature, he click OK to run the file with the selected application

for example:
the user click on KML file from firefox web page, now
if Google Earth is already installed, the user will click to run the files on the "Open with" ui (like to day),
but if Google Earth is not install the "Open with, Other" will be the user option,
after the user OK the os pop up this UI,
now the user need to mark from the recommend application list, Google Earth to install it and run it with the KML file

on why Wishlist
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135251](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135251)

---

### Post by lexen on 2008-01-05
Sounds like a nice idea, I wonder how hard it would be to do this.  You would have to have some connection between nautilus and synaptic.

---

### Post by Rufe0 on 2008-01-06
I agree

---

### Post by toppavak on 2008-01-07
"You would have to have some connection between nautilus and synaptic."

Couldn't it just search through the files used to generate the application lists in the gnome main menu and compare that to a list in a text file of 'recommended' applications for a certain file extension? Then it could recommend installing such and such application from that list in order to open that file and (with user approval) fetch the corresponding package(s) using synaptic / add-remove applications.

---

