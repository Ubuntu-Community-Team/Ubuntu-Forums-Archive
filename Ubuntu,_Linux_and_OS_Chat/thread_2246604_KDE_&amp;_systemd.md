---
title: "KDE &amp; systemd"
date: 2014-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-10-01
I'm just wondering about how KDE-based systems will deal with systemd in the future because, from whatever I've read, systemd is closely tied in with GNOME stuff.

---

### Post by sammiev on 2014-10-02
> **vasa1 said:**
> I'm just wondering about how KDE-based systems will deal with systemd in the future because, from whatever I've read, systemd is closely tied in with GNOME stuff.

Actually your very correct on that. I think I will add myself to this thread.

Thanks vasa1 for picking up on that.

---

### Post by vasa1 on 2014-10-02
> **sammiev said:**
> Actually your very correct on that. I think I will add myself to this thread.

Thanks vasa1 for picking up on that.
You're welcome. I couldn't find anything on the topic. Maybe it's early days?

---

### Post by Tadaen_Sylvermane on 2014-10-02
It's more along the lines of the Gnome people making Gnome require systemd than the other way around. Reality is it's just an init system, better in some ways and worse in others to sysvinit. I can't imagine that systemd will pick a favorite DE, Gnome in particular as it is not well liked by the majority of people.

*EDIT* For the record I don't understand init systems in the slightest. My post reflects only the varying viewpoints I have seen scattered across various forums.

---

### Post by rrnbtter on 2014-10-02
Greetings,
I don't get the problem! Systemd is not default in any version. It is being tested with Utopic and works really well. There are daily updates so it is being adapted to Canonical's needs. There is a learning curve with the command set but everything else has been smooth as silk. Actually, I see systemd's purpose as enabling Canonical to better position itself in the server market where it is struggling.

Edit: incidentally! I expect that systemd will work just fine with KDE when it is final. I have never used KDE but I love the software especially K3B which I wouldn't want to do without.

---

### Post by Morbius1 on 2014-10-02
The developer of systemd is one smart cookie. Anticipating that there would be a war over systemd he took measures a long time ago to make systemd a [dependency of Gnome]("https://mail.gnome.org/archives/desktop-devel-list/2011-May/msg00427.html") insuring his side would win regardless of the politics or technical arguments.

In any event since the desicion was made to go to systemd KDE will have to comply.

---

### Post by rrnbtter on 2014-10-02
Greetings,

> **Morbius1 said:**
>  [dependency of Gnome]("https://mail.gnome.org/archives/desktop-devel-list/2011-May/msg00427.html") 

This article is an example of exactly my point. The signing on by Redhat for it's server market gave systemd momentum. All the rest is trinkle down, Fedora, Suse, etc and Ubuntu falling into line as the last big hold-out. As a Ubuntu Unity Desktop user I will say that I am pleased with the result. Those looking for a more simplistic approach may possibly be disappointed [but not sure about this]. Many of the oldest experienced users on the forum don't know for sure where all of this will end, especially with Mir and Unity 8. For the most part I am happy.

---

### Post by vasa1 on 2014-10-02
@rrnbtter, I started this thread to know what how KDE distros will deal with systemd or whether any discussion has taken place on this specific issue.

---

### Post by oldos2er on 2014-10-02
I ran openSuse 13.1 KDE for several months with no issues; worked just fine.

---

### Post by rrnbtter on 2014-10-05
Greetings,
@vasa1, If you want to know the answer to your question install the kubuntu 14.10 ISO then run updates. After the install open a terminal and type "sudo apt-get install -s systemd-sysv" then edit your /etc/default/grub and change your grub command line to look like this GRUB_CMDLINE_LINUX="quiet splash init=/lib/systemd/systemd", then update grub "sudo update-grub". reboot. You should then be in business with systemd. 

I personally installed the stable Plasma4 edition of kubuntu and not the testing Plasma5. I'm not a kubuntu user so i'm not at ease with the system but it seemed to work really well.  I only did the install to answer your question and can tell you that systemd is very robust and stable on this intel chipset. 

As to the "future" part of your statement I can only tell you that I like Linux but I don't do crystal balls. It is however working now.

---

