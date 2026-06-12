---
title: "Awoken icon theme?"
date: 2012-05-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by codingman on 2012-05-01
When I try to add the person who made the Awoken icon theme to my repos, and then i update,it looks for the repos through the quantal link which currently does not include the repos. Is it possible to hook that up to the Precise repos instead?

My code is:


 sudo add-apt-repository ppa:alecive/antigone
 sudo apt-get update
sudo apt-get install awoken-icon-theme

The last one was the one I was about to do but then noticed the second line of code gave me this error:

W: Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found


Any help would be appreciated!

---

### Post by lonniehenry on 2012-05-01
The PPAs will not have Quantal in them yet.  Change the version to Precise for the moment.

---

### Post by ScislaC on 2012-05-01
The PPAs can build for Quantal already, it just needs to be enabled (via the recipes page). I already did it for two PPAs the other day.

---

### Post by Harry33 on 2012-05-02
> **codingman said:**
> When I try to add the person who made the Awoken icon theme to my repos, and then i update,it looks for the repos through the quantal link which currently does not include the repos. Is it possible to hook that up to the Precise repos instead?

...

Any help would be appreciated!

Yes you can use the PPA and its Precise branch very well.
Quantal is actually very much like Precise for a long time and works well with Precise packages.

---

### Post by codingman on 2012-05-02
But how can I make the computer search for the precise repos instead of the quantal repos?

Cause as you saw my first post, it gives me an ugly 404

---

### Post by lonniehenry on 2012-05-02
If you use software center, start it and go to edit, software sources, click on other software. Highlight the line with the ppa you want, click edit, and change the distribution line to precise and click ok.  Do this for all your ppas.  If you use synaptic, do the same in sources there.

---

### Post by Harry33 on 2012-05-03
> **codingman said:**
> But how can I make the computer search for the precise repos instead of the quantal repos?

Cause as you saw my first post, it gives me an ugly 404

You can also manually edit sources.list file

```
gksu gedit /etc/apt/sources.list
```

and from the appropriate PPA line replace the word quantal with the word precise.

---

### Post by codingman on 2012-05-04
> **lonniehenry said:**
> If you use software center, start it and go to edit, software sources, click on other software. Highlight the line with the ppa you want, click edit, and change the distribution line to precise and click ok.  Do this for all your ppas.  If you use synaptic, do the same in sources there.
Thank you! That really helped. I guess I learned a valuable lesson ;)

---

### Post by lonniehenry on 2012-05-05
You should check the PPAs sometime around alpha 1 or 2 to see if they have caught up and added a quantal section. If they have then just change the precise to quantal as before to get any new things they have been working on.

---

