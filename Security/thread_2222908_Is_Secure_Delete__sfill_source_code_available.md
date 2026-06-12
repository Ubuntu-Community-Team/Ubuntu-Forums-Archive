---
title: "Is Secure Delete / sfill source code available?"
date: 2014-05-08
forum: Security
---

### Post by PopsTheSailor on 2014-05-08
Does anyone know if the source code is available for Secure Delete, specifically, sfill. I want to update it to give a better procress status above just putting a "*" when one pass is complete.

I'd like to have it show pass and a counter or something to show progress within the pass.

---

### Post by cariboo on 2014-05-08
THe source for all open source packages are available in the repositories, make sure you have sources enabled in /etc/apt/sources list, the update the source list:

```
sudo apt-get update
```

then download the source:

```
sudo apt-get source secure-delete
```

---

### Post by PopsTheSailor on 2014-05-09
When I add the sources to my repos and then try the sudo apt-get update, I get the following errors. I did a fresh reboot and went straight to terminal to try this without starting anything else.

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by cariboo on 2014-05-09
Make sure you don't have update-manager or the Software Centre open.

---

### Post by PopsTheSailor on 2014-05-10
The only way I know how to enable sources is to do it with a check box in the update-manager. How do I do it without having it open? Do I edit a file manually? Which one? What "code" do I put in the file?

---

### Post by cariboo on 2014-05-10
Have a look at /etc/apt/sources.list any line starting with a # symbol is commented out, and won't be accessed, remove the # at the start of the line for the repositories you want to enable.

You must edit the file with elevated privileges, so you need to use sudo, eg:

```
sudo nano /etc/apt/sources.list
```

---

### Post by oldos2er on 2014-05-11
Just FYI, "sudo" is unnecessary when using ```
apt-get source <package>
```

---

