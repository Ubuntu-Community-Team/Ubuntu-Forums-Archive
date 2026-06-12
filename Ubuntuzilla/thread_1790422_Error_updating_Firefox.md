---
title: "Error updating Firefox"
date: 2011-06-25
forum: Ubuntuzilla
---

### Post by thenudehamster on 2011-06-25
I have only one of  my four Ubuntu (all on 11.04) equipped machines running Ubuntuzilla, and until Firefox was updated to 5.0, I never really noticed a problem but the U-zilla machine does not update beyond 3.5.5. Trying to update or reinstall with apt-get I get an error telling me that the package has been diverted by a third-party installer;
 "/usr/bin/firefox has been diverted by a third party package which didn't specify
a package name to dpkg-divert. This is usually as a result of installing unsupported
packages from Ubuntuzilla.
***This is a BUG. Please report this bug to the vendor of the third party package you installed***"
Even after removing Ubuntuzilla (which no longer seems necessary) I still get the same problem.

So. How do I cure this and get my system to update Firefox properly?

---

### Post by lovinglinux on 2011-06-25
Ubuntuzilla is no longer under development. 

Try this:

```
sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
```

Then update your Firefox from the repos, which is already version 5 in Natty.

If you want the latest beta versions of Firefox, use a mozillateam ppa instead. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by thenudehamster on 2011-06-25
> **lovinglinux said:**
> Ubuntuzilla is no longer under development. 

Try this:

```
sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
```

Then update your Firefox from the repos, which is already version 5 in Natty.

If you want the latest beta versions of Firefox, use a mozillateam ppa instead. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

Thank you so much for your advice. 
I gathered that Ubuntuzilla is no longer active, but this machine was first set up on 9.04, when U-zilla was almost essential for prompt updates.
 
I had spent several hours trying to implement the advice from another thread which was dealing with a similar problem, but always came up against that dpkg diversion, which I had no idea how to deal with. Your simple few lines of code cured the problem and I now have Firefox 5 on all my machines.

Thank you again

---

### Post by lovinglinux on 2011-06-25
> **thenudehamster said:**
> Thank you so much for your advice. 
I gathered that Ubuntuzilla is no longer active, but this machine was first set up on 9.04, when U-zilla was almost essential for prompt updates.
 
I had spent several hours trying to implement the advice from another thread which was dealing with a similar problem, but always came up against that dpkg diversion, which I had no idea how to deal with. Your simple few lines of code cured the problem and I now have Firefox 5 on all my machines.

Thank you again

You are welcome.

---

### Post by Karlchen on 2011-06-26
[QUOTE=lovinglinux]Ubuntuzilla is no longer under development.[/QUOTE]This is what [nanotube announced a while ago]("http://ubuntuforums.org/showthread.php?t=1700967"). Yet, I am not quite sure whether it is completely dead, because my Lucid Lynx (10.04.2) has received the Mozilla Thunderbird update v3.1.11 today. - I know this thread is about Firefox, not Thunderbird, but Ubuntuzilla used to provide updates for both. - Moreover, Synaptic tells me that both, Firefox-Mozilla-Build v5.0 and Thunderbird-Mozilla-Build v3.1.11, are available in nanotube's Ubuntuzilla repository.

Karl

---

### Post by nanotube on 2011-07-11
> **Karlchen said:**
> This is what [nanotube announced a while ago]("http://ubuntuforums.org/showthread.php?t=1700967"). Yet, I am not quite sure whether it is completely dead, because my Lucid Lynx (10.04.2) has received the Mozilla Thunderbird update v3.1.11 today. - I know this thread is about Firefox, not Thunderbird, but Ubuntuzilla used to provide updates for both. - Moreover, Synaptic tells me that both, Firefox-Mozilla-Build v5.0 and Thunderbird-Mozilla-Build v3.1.11, are available in nanotube's Ubuntuzilla repository.

Karl

yes, i have been updating it after all. ubuntu lucid hasn't been following the most recent mozilla releases... though i assumed it would since the "new policy" was to do so. so i suppose ubuntuzilla will continue to get the latest mozilla releases.

"the rumors of ubuntuzilla's death have been greatly exaggerated" ? hehe.

---

