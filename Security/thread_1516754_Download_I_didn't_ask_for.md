---
title: "Download I didn't ask for?"
date: 2010-06-24
forum: Security
---

### Post by jaxtabram on 2010-06-24
jaunty jackalope.

Two weeks ago a window popped up and said restart was needed to install download ...can't remember exact words.

I wasn't downloading anything.
It didn't ask me or tell me anything other than this.
Is this normal?
Concerned.
Thanyou.

---

### Post by Rubi1200 on 2010-06-24
Have you noticed any unusual activity since then?

Are there hidden files or folders which were not there before?

Have you cleared out your browser history and cookies?

---

### Post by jaxtabram on 2010-06-24
> **Rubi1200 said:**
> Have you noticed any unusual activity since then?

Are there hidden files or folders which were not there before?

Have you cleared out your browser history and cookies?

I'm a bit of a novice with Linux.
Nothing untoward happening.
I had gotten involved with a very heavy duty argument re the Israeli killings of people on the boat.
It then spilled into Zionism and became very very heavy.
Within 48 hrs I get this mysterious download.
Never happened before.

Before anything is installed I have to type password in.
Not this time.

I only use this pc for email and  political discussion on forums.
That's all.

Am I getting paranoid in my old age?

---

### Post by Ryan Dwyer on 2010-06-24
It would have been a security update that got downloaded and installed automatically as per your settings in System > Administration > Software Sources > Updates tab.

---

### Post by jaxtabram on 2010-06-24
> **Ryan Dwyer said:**
> It would have been a security update that got downloaded and installed automatically as per your settings in System > Administration > Software Sources > Updates tab.

It's set so that I always get asked though and have to type my password in ...that's why I'm a little disturbed by it.
It's never happened before.

---

### Post by Rubi1200 on 2010-06-24
> **Ryan Dwyer said:**
> It would have been a security update that got downloaded and installed automatically as per your settings in System > Administration > Software Sources > Updates tab.

Exactly; have a look and if the Install security updates without confirmation button is checked, then there is your answer.

Oops: cross posting

---

### Post by TBABill on 2010-06-24
Or it could have been an attempt by a website to download to your machine via popup. Sometimes if you click certain points on websites you will be offered a download or have a file automatically try to download. Fortunately, on Ubuntu or any Linux distro the files are harmless because they are most likely .exe Windows executable files that cannot execute on your machine. Depending on where your downloads go (normally the downloads folder under home>you>Downloads) you can scan through your downloaded files and see if any are there. I have had this happen and I click "no" in my browser to the download but if you clicked yes or if it just downloaded on its own, the file should be there if it did in fact download.
 
Should be harmless on your machine if it did get through but most likely it was just an attempt to get through that you clicked no to.

---

### Post by Rubi1200 on 2010-06-24
Which is why it is probably a good idea to clear out browser history and cookies.

---

### Post by jaxtabram on 2010-06-24
> **Rubi1200 said:**
> Which is why it is probably a good idea to clear out browser history and cookies.

I'll do that now ...thankyou.

---

### Post by OpSecShellshock on 2010-06-24
Was it asking you to restart your computer or just your browser? Add-ons for Firefox automatically update all the time and require the application to be restarted. As far as the installation of other software on your computer itself, you really would have to elevate your privileges in order for it to work. You may have just run across a compromised web page somewhere that redirects to code that's made to trick Windows users into installing malware. Happens all the time.

I really don't think your argument had anything to do with it.

---

### Post by jaxtabram on 2010-06-24
> **OpSecShellshock said:**
> Was it asking you to restart your computer or just your browser? Add-ons for Firefox automatically update all the time and require the application to be restarted. As far as the installation of other software on your computer itself, you really would have to elevate your privileges in order for it to work. You may have just run across a compromised web page somewhere that redirects to code that's made to trick Windows users into installing malware. Happens all the time.

I really don't think your argument had anything to do with it.

PC ...I din't have my browser open.
I only had desk top up at the time as I was sat at my desk stuffing my face when the window popped up.
It's niggled me ever since.

---

### Post by nerdy_kid on 2010-06-24
i would check /var/log/auth.log and /var/log/dpkg.log and /var/log/apt/history.log for suspicious entries.  Also, how strong is your password? and do you have a firewall running?

---

### Post by jaxtabram on 2010-06-24
> **nerdy_kid said:**
> i would check /var/log/auth.log and /var/log/dpkg.log and /var/log/apt/history.log for suspicious entries.  Also, how strong is your password? and do you have a firewall running?

Firewall yes ....Gufw 0.20.7
Strong password yes.
Firewall can't even run without password.

---

### Post by jaxtabram on 2010-06-24
Just curious ...if someone wanted to monitor a protester could they download something onto my pc so easily?
Thanks for the replies so far everyone.

---

### Post by Keith_K on 2010-06-24
While I believe that the simplest explanation is the most likely, a little bit of paninoia is not necessarly a bad thing.You did experience something that was out of the ordinary and it should be investigated. However, two weeks is a long time to start investigating and logs could have been replaced since then with normal activity. 
I'm new to ubuntu also, but for your piece of mind, you might want to step through an intrusion detection routine, if you haven't already. I've just recently started this and am using tiger. [You can read up on it here]("http://ubuntuforums.org/showpost.php?p=9265631&postcount=6")

---

### Post by jaxtabram on 2010-06-24
> **Keith_K said:**
> While I believe that the simplest explanation is the most likely, a little bit of paninoia is not necessarly a bad thing.You did experience something that was out of the ordinary and it should be investigated. However, two weeks is a long time to start investigating and logs could have been replaced since then with normal activity. 
I'm new to ubuntu also, but for your piece of mind, you might want to step through an intrusion detection routine, if you haven't already. I've just recently started this and am using tiger. [You can read up on it here]("http://ubuntuforums.org/showpost.php?p=9265631&postcount=6")

Thanks ...yes two weeks is a long time to have left it.
It has niggled away at me and I forgot about this place too till it dawned on me this morning.
I'll have a look at the link.

---

### Post by OpSecShellshock on 2010-06-24
> **jaxtabram said:**
> Just curious ...if someone wanted to monitor a protester could they download something onto my pc so easily?
Thanks for the replies so far everyone.

The short answer is probably not. The more specific the target, the more effort is required.

---

