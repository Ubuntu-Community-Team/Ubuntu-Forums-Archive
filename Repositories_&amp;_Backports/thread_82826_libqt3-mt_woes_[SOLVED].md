---
title: "libqt3-mt woes [SOLVED]"
date: 2005-10-27
forum: Repositories &amp; Backports
---

### Post by No_Code on 2005-10-27
I was trying to install fwbuilder and a few other utilities over the past few days that happened to rely on the libqt3-mt package, but Synaptic and apt-get would never allow me to install it, throwing some kind of a versioning error. Of course, this was my own fault as I had forgotten to update my sources.list file to reflect the new Breezy repositories when I went from Hoary to Breezy (btw, MAD props to the Ubuntu devs for making that process as quick and painless as possible :D ).

So, if you're having any issues with that particular package, do the following:

1. sudo gedit /etc/apt/sources.list
2. Enter your password
3. Do a search and replace to replace **hoary** with **breezy**.
4. Save the file
5. sudo apt-get update
6. Enjoy!

**Note:** If you have any non-standard repositories in your sources.list file, your mileage may vary with this method as those repositories may or may not have Breezy packages on them.

---

