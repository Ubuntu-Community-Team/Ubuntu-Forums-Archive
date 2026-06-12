---
title: "add a link to sources.list"
date: 2005-09-21
forum: Repositories &amp; Backports
---

### Post by Josef K. on 2005-09-21
I was looking for a new version of sylpheed claws and I find on the home-page this [Unofficial Ubuntu Hoary packages](http://claws.sylpheed.org/ubuntu/) 
but it seems doesn't have the usual structure of a repository (a directory name dist etc.) so synaptic doesn't accept the link

I know I can simply download deb files and install them directly but I wonder how can I add to sources.list a simple directory that doesn't have the *correct* structure?

---

### Post by banadushi on 2005-09-21
Since they dont' provide a Release and Packages files, I'm pretty sure you can't add it as a repo for apt, so your kinda SOL there.  For other sites that do have a Release and Packages files in the same dir as the debs you can put:

```

deb http://example.org/ubuntu ./

```

in your sources.list.

Have a good one!

Jason

---

### Post by colinleroy on 2005-12-06
You can now use
deb [http://claws.sylpheed.org/ubuntu/breezy/](http://claws.sylpheed.org/ubuntu/breezy/) ./

---

### Post by teaker1s on 2005-12-06
in synaptic add custom and put the web address in or

sudo gedit /etc/apt/sources.list

---

