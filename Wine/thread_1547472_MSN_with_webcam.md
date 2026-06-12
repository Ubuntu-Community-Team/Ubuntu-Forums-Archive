---
title: "MSN with webcam"
date: 2010-08-06
forum: Wine
---

### Post by junke1990 on 2010-08-06
Heey guys 

I've found this:
[http://wiki.winehq.org/MSN_Messenger_webcam_support](http://wiki.winehq.org/MSN_Messenger_webcam_support)

and downloaded the MSN versions here:
[http://www.brothersoft.com/msn-messenger-download-244851.html](http://www.brothersoft.com/msn-messenger-download-244851.html)

both 6.2 and 7

and followed the instructions, however 7 (and 8.5) cant find my cam and 6.2 isn't able to connect because I get this message in terminal:

fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!

So after gooogling I found this:
[http://wine.1045685.n5.nabble.com/Msn-9-td1696810.html](http://wine.1045685.n5.nabble.com/Msn-9-td1696810.html)

and tried the bottom solution:
Native urlmon and

```
wget kegel.com/wine/winetricks && sh winetricks ie6
```

none of it all is successful... anyone else who did succeed????

---

### Post by cogadh on 2010-08-06
Is there a reason you have to use MSN via Wine instead of one of the many Linux native MSN alternatives? If webcam functionality is your main concern, I believe [aMSN]("http://www.amsn-project.net/index.php") already supports it.

---

### Post by junke1990 on 2010-08-07
I am using amsn but amsn has a big big downside, for the cam and the filetransfers to work it requires port forwarding if you are withing a NAT. Besides that a lot of the times I'm not able to watch and cast the cam at the same time. There for I would like to try MSN messenger.

---

### Post by Beren Camlost on 2010-08-07
There's Kopete, but unsure if it works with Gnome.

---

### Post by junke1990 on 2010-08-07
as far as I can see, it doesnt support cam for the msn protocol

---

### Post by FlameReaper on 2010-08-28
> **cogadh said:**
> Is there a reason you have to use MSN via Wine instead of one of the many Linux native MSN alternatives? If webcam functionality is your main concern, I believe [aMSN]("http://www.amsn-project.net/index.php") already supports it.

Majority doesn't, but I suppose a minority does.

As for me the main reason why I'd still want to use Windows Live Messenger is because of this feature, quoted from softpedia:

> Microsoft is flexing the social networking muscles of its instant messaging client with the latest release. Windows Live messenger 9.0 (2009)  brings to the table a feature dubbed **Groups, designed to extend the communication capabilities of the client beyond one-on-one conversations, now helping groups of users talk, collaborate, and share. **According to the Redmond company, public Windows Live Messenger Groups is not designed as an alternative to community forums, or to affiliation groups, social networks with millions of users, it is rather a limited service for its initial release set up to streamline conversations between multiple Windows Live Messenger users.

“Windows Live continues to extend and improve upon [the communication] experience with new, integrated features that help you keep your life in sync, while staying in touch with the people you care about. With the new Windows Live Groups, we’ve released a set of simple tools to help you communicate and share with the 'real world' groups that so many of us belong to: sports teams, school committees, neighborhood associations, scout troops, etc,” a member of Windows Live team revealed.

Windows Live Messenger 9.0 (2009) Groups
Enlarge picture
In Windows Live Messenger 9.0 (2009), and this is also valid for the latest Beta Refresh release, groups can be put together via the Add menu, the option just under Add a Contact, namely Create a Group. Users need only label the new Group, and then select friends from the contacts list to be added. Moreover, they will be able not only to have group conversations, but also to share calendars and even photos via Windows Live Messenger.

**“A unique feature of Windows Live Groups is that the groups you create will automatically show up in Messenger. For smaller groups (up to 20 people), you can even have group conversations with whomever happens to be online,” the Windows Live team representative added. “Of course, as the owner of a group, you can turn off the Messenger conversation feature, if that’s what your members prefer, or if the group grows to more than 20 people – just click Options on your group’s website, and then click Edit Settings.”**


The bolded feature is still unavailable in *any* of the Linux alternatives so far - yada, nilch, zero.

In fact, that's the only reason I still use WLM till today, because my circle of friends communicate via the WLM Groups feature. Else I'd kiss goodbye to WLM already.

And just to drive my point further, I have used both aMSN and emesene but I'm not very satisfied because of this missing feature. Same goes to the other multi-protocol IMs such as Pidgin, Empathy etc. Yada, nilch, zero.

I just hope the current WLM alternatives can implement that somehow.

---

### Post by xtremesupremacy3 on 2010-10-18
As it is this is status for most Linux native programs:

Empathy: Theres more missing than available (why use it? i dunno) no webcam for MSN
Pidgin: No webcam or voice for MSN, but is available for Google for instance
aMSN: Have stopped webcam due to Microsoft restrictions
Emesene: Has all features that Windows Live Messenger has (webcam + voice) without changing router settings.


I tested these on Sunday 17th October 2010. I can't speak for the KDE based programs due to me running Gnome.

Hope that helps somewhat

---

### Post by junke1990 on 2010-10-18
I tried emesene 1.6 but it failed to connect, 2.0 beta didn't even log in properly.

---

### Post by xtremesupremacy3 on 2010-10-18
I am currently using Emesene 1.6.3 which I got from the repositories and I am not having any problems connecting.

Perhaps the problem may lay with your router?

I must say however, I used to have very poor initial connection to many services including MSN related clients. This was resolved by changing DNS (opendns). I hope that may point you towards a positive result

---

