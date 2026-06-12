---
title: "Installing vmware-view-client (depency issues)"
date: 2013-09-11
forum: Virtualisation
---

### Post by jamesisin on 2013-09-11
I have the Canonical Partners repository enabled as instructed.  When I attempt to install vmware-view-client I get this:

```
sudo apt-get install vmware-view-client
[sudo] password for ME: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vmware-view-client:i386 : Depends: libudev0:i386 (>= 147) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

The error mentions i386 so perhaps running 64 bit Ubuntu is the trouble?  I don't know.

Anybody install this client?

---

### Post by jamesisin on 2013-09-13
So I built a 32 bit machine (also 13.04) and enabled the Partners repository.  This is what I get on that build:

```
sudo apt-get install vmware-view-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vmware-view-client : Depends: libudev0 (>= 147) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by jamesisin on 2013-09-15
Anybody?

---

### Post by jamesisin on 2013-09-18
No love?

---

### Post by jamesisin on 2013-10-22
Am I the only person interested in this application/protocol?

---

### Post by KillerKelvUK on 2013-10-25
Hi, I'm interested in finding out how View works out for you so hope you come back with more info or a pm.  Your post showed the error and a possible resolution as I've quoted below.

> **jamesisin said:**
> 
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vmware-view-client : Depends: libudev0 (>= 147) but it is not installable
E: Unable to correct problems, you have held broken packages.[/CODE]

A quick google search for libudev0 and you find this [http://productforums.google.com/forum/#!topic/chrome/FyszF27mzIc](http://productforums.google.com/forum/#!topic/chrome/FyszF27mzIc) post as the 2nd hit...

Reads like VMWare need to update their packing for the View client but a work around is to install the libudev0 package which you can download from the link in the above noted thread.

Give it a try and post back you results, best of luck.

---

### Post by jamesisin on 2013-11-05
Do you know how to file a bug report with VMWare?

---

### Post by houstonbofh on 2013-11-06
I have been using the VMware View Open Client with no issues at all.  It is fast, stable, and more frequently updated.

```
sudo apt-get install vmware-view-open-client
```

---

### Post by jamesisin on 2013-11-06
The open client doesn't support PCoIP (only RDP so just use Remina).

---

