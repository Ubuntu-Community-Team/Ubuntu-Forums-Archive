---
title: "Lost Firewall"
date: 2012-06-26
forum: Security
---

### Post by bencouve on 2012-06-26
I appear to have lost my firewall. May have accidentally removed it in the last few days. Would anyone know how I re-install/down load firewall.

Thanks in advance.

---

### Post by vasa1 on 2012-06-26
> **bencouve said:**
> I appear to have lost my firewall. May have accidentally removed it in the last few days. Would anyone know how I re-install/down load firewall.

Thanks in advance.
What is its name? ???

---

### Post by haqking on 2012-06-26
> **bencouve said:**
> I appear to have lost my firewall. May have accidentally removed it in the last few days. Would anyone know how I re-install/down load firewall.

Thanks in advance.

That would be impossible as the firewall is hardcoded into the kernel and its called Netfilter controlled by IPTables.

YOU have probably deleted the front end which you use such as UFW/GUFW or Firestarter.

If it was firestarter then dont bother reinstalling it as it is out of date and buggy.

What do you think you removed and how ?

type

```
sudo ufw status
```

Peace

---

### Post by bencouve on 2012-06-26
> **haqking said:**
> 

```
sudo ufw status
```Peace


and the result is 

Status: inactive

---

### Post by haqking on 2012-06-26
> **bencouve said:**
> and the result is 

Status: inactive

if it wasnt there it wouldnt say that at all so type the following to re-enable it:

```
sudo ufw default deny
``````
sudo ufw enable
``````
sudo ufw status
```

---

### Post by bencouve on 2012-06-26
> **haqking said:**
> That would be impossible as the firewall is hardcoded into the kernel and its called Netfilter controlled by IPTables.

YOU have probably deleted the front end which you use such as UFW/GUFW or Firestarter.




Ok, I have followed your instructions and get "Firewall is active and enabled on system startup" . How do I get the front end back ?

---

### Post by haqking on 2012-06-26
> **bencouve said:**
> Ok, I have followed your instructions and get "Firewall is active and enabled on system startup" . How do I get the front end back ?

Well that means it is working as it should.

As for your front end, i dont know ? What were you using ?

UFW is command line as is IPTables.

Did you previously have GUFW which is the GUI for UFW ?

Is it no longer on your menu then ?

what happens when you launch it from terminal with

```
gufw
```

or

```
gksudo gufw
```

---

### Post by Frogs Hair on 2012-06-26
GUFW should also appear as Firewall Configuration in dash if you didn't remove it.

---

### Post by bencouve on 2012-06-26
> **Frogs Hair said:**
> GUFW should also appear as Firewall Configuration in dash if you didn't remove it.

It had disappeared from the dash. Normally I can type Firewall and it appears again. Anyway, it is back. Can't seem to drag and drop it into the list of applications on the left of my screen. However, that is ok. 

Thanks for your help. Always appreciated.

TYVM !!!

---

### Post by haqking on 2012-06-26
> **bencouve said:**
> It had disappeared from the dash. Normally I can type Firewall and it appears again. Anyway, it is back. Can't seem to drag and drop it into the list of applications on the left of my screen. However, that is ok. 

Thanks for your help. Always appreciated.

TYVM !!!
  Your welcome.

remember to use the thread tools to mark the thread as solved.

Cheers

---

### Post by Frogs Hair on 2012-06-26
When you open the application and the icon appears in the launcher, right click the icon and choose "lock to Launcher."

---

### Post by bencouve on 2012-06-26
The thread tools is a good point as I have not actually used this yet. 

Have just one last question.

If this version of firewall is obsolete then can you recommend one, and a freebee if possible.

Thanks in advance.

---

### Post by oldos2er on 2012-06-26
Moved to Security Discussions.

---

### Post by haqking on 2012-06-26
> **bencouve said:**
> The thread tools is a good point as I have not actually used this yet. 

Have just one last question.

If this version of firewall is obsolete then can you recommend one, and a freebee if possible.

Thanks in advance.

I said firestarter is out of date a buggy project (though if it works it works so to speak) you appear to be using UFW and GUFW.

UFW is the default firewall interface for Ubuntu, so unless you are using firestarter then carry on as you are.

Peace

---

