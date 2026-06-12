---
title: "Unable to install security updates after installing Virtualbox."
date: 2011-02-18
forum: Virtualisation
---

### Post by panderohit on 2011-02-18
Hi. I recently installed Virtualbox 4.0.2 from their website. Thereafter my computer refuses to upload security updates. 

When I click 'Check' it says: "Failed to download repository information. Check your Internet connection." and the message box says:

"W:GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139, W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/contrib/source/Sources.gz](http://download.virtualbox.org/virtualbox/debian/dists/maverick/contrib/source/Sources.gz)  404  Not found
, E:Some index files failed to download, they have been ignored, or old ones used instead."

Thereafter, clicking Install Updates, prompts: "Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources.."

and the details box says: "virtualbox-4.0"

The output for sudo apt-get update is:

Err [http://download.virtualbox.org](http://download.virtualbox.org) maverick/contrib Sources                    
  404  Not found
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Fetched 198B in 2s (90B/s)
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/contrib/source/Sources.gz](http://download.virtualbox.org/virtualbox/debian/dists/maverick/contrib/source/Sources.gz)  404  Not found

E: Some index files failed to download, they have been ignored, or old ones used instead.


I know that I have not done something right. Earlier, when installing from the website, I had opened: /etc/apt/sources.list 

There, I clicked on 'Other Software', then 'Add' and in the apt line I entered: 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib

This added two repositories:
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib (Source code)


What am I missing?

Thanks and regards.

---

### Post by Old_Grey_Wolf on 2011-02-19
Run these commands to get the GPG key that you are missing
```
gpg --keyserver keyserver.ubuntu.com --recv 54422A4B98AB5139
gpg --export --armor 54422A4B98AB5139  | sudo apt-key add -
```

---

### Post by panderohit on 2011-02-19
Hi Old_Gray_Wolf

Thanks a lot for your help. I did this but the update manager still continues to give the same responses to Install Updates and Check as mentioned above, namely:

> When I click 'Check' it says: "Failed to download repository  information. Check your Internet connection." and the message box says:

"W:GPG error: [http://download.virtualbox.org]("http://download.virtualbox.org/")  maverick Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 54422A4B98AB5139, W:Failed  to fetch [http://download.virtualbox.org/virtu...rce/Sources.gz]("http://download.virtualbox.org/virtualbox/debian/dists/maverick/contrib/source/Sources.gz")  404  Not found
, E:Some index files failed to download, they have been ignored, or old ones used instead."

Thereafter, clicking Install Updates, prompts: "Requires installation of  untrusted packages. The action would require the installation of  packages from not authenticated sources.."

and the details box says: "virtualbox-4.0"

Is there anything else that I am missing?

---

### Post by Old_Grey_Wolf on 2011-02-19
It looks like the server you are using is not responding; therefore, the 404 error.

Get into Synaptic Package Manager and go to the menu "Settings > Repositories"; then, select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

I doubt you need the Virtualbox source code; therefore, remove that from your sources via Synaptic (un-check the boxes next to the Virtualbox entries).

Then try updating again.

If it still gives you the massage about installing untrusted packages, then post the exact output of the error here.

---

### Post by panderohit on 2011-02-19
Hi.

I did what you suggested and on clicking 'Reload', it gave the following error:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

And then clicking 'Check' on update gives the same error as before:

> Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  contrib/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Old_Grey_Wolf on 2011-02-19
You did the following > There, I clicked on 'Other Software', then 'Add' and in the apt line I entered:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib

This added two repositories:
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib (Source code)



I get updates for Virtualbox without adding it to Synaptic.

Remove those entries from Synaptic and try updating again.

-

If you are still having problems and I don't respond, it is because I am sleeping for the night.

---

### Post by panderohit on 2011-02-19
Thank you. I have done this and the Update Manager behaves alright. I hope the updates for virtualbox come through like they do for you.

Regards.

---

### Post by Old_Grey_Wolf on 2011-02-20
I guess you followed the instructions from this page. [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I used gedit to add the deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib to the sources.list.

I was getting notifications of updates when I started Virtualbox, and had to go to their website to download them. Now that I added the line to sources.list, the updates happen automatically.

---

### Post by panderohit on 2011-02-20
Hi. Yes that's what I used. I'm not aware of the usage of gedit. Would it please be possible for you to send me the instructions on how to use gedit? Thanks a lot.

---

### Post by Old_Grey_Wolf on 2011-02-20
> **panderohit said:**
> Hi. Yes that's what I used. I'm not aware of the usage of gedit. Would it please be possible for you to send me the instructions on how to use gedit? Thanks a lot.

Gedit is like a text editor. It is easy to use. You will need to type this command in the terminal to edit the sources.list file.```
gksudo gedit /etc/apt/sources.list
```

At the bottom of the file paste in this line and save the file.
```
deb http://download.virtualbox.org/virtualbox/debian maverick contrib
```

---

### Post by panderohit on 2011-02-21
Yeah. I did that and it works beautifully. I got the update. Thanks a lot for your help. Cheers.

---

