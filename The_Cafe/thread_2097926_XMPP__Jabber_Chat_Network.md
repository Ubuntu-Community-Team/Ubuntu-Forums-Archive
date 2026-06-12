---
title: "XMPP \ Jabber Chat Network"
date: 2012-12-24
forum: The Cafe
---

### Post by Kirk Schnable on 2012-12-24
I am looking for some input and ideas on this thought I've had for awhile, and I can't think of a better group of people to discuss this with than the intelligent users here at the Ubuntu Forums.

For the past several years, I have corresponded with my friends online, largely using consumer services whose true privacy\security is somewhat ambiguous (AOL Instant Messenger, MSN\Windows Live Messenger, Skype, etc).  

In today's environment, with treaties like ACTA and TPP on the table, [credible NSA whistleblowers telling us that everyone in the USA is being spied on]("http://www.youtube.com/watch?v=TuET0kpHoyM"), and [conversations that recent infrastructure changes to Skype may make it easier for conversations to be wiretapped]("http://www.extremetech.com/computing/132935-microsoft-tweaking-skype-to-facilitate-wiretapping"), I have made the decision to only trust private conversation to SSL encrypted IRC channels.

Unfortunately, it's difficult for me to convince some of my close, yet not necessarily tech-savvy friends of the benefits of IRC, because it's a relatively clunky and difficult-to-use protocol for the non-technically-inclined.

My friends and I also really enjoy the features of Skype, like their ability to have audio\video calls, conference calls, text chat, and other cool features like desktop sharing all built in to their IM client.  And, when having conversations about pop culture, movies, music, etc, it's probably fine to keep using consumer services like Skype.  But I personally am not very comfortable using these services for private conversation anymore.

I'm looking for a solution that will enable me to move some of my less tech savvy friends to a new, more secure form of communication.  This quest has led me to Jabber\XMPP over and over again.  XMPP seems to be a fantastic way to start your own chat network, and is even versatile enough to interact with other chat networks.

Where I think XMPP has been falling short is with the maturity of the clients.  Clients like Pidgin and Empathy do support XMPP, but in my testing, I had problems with Pidgin clients on Windows supporting the multimedia features I was looking for.

I am looking for a solid client solution that will work well cross-platform (at least on Windows and Linux) and will use the XMPP resources to provide the type of multimedia features found in Skype.

This search led me to Jitsi.  It seems like the Linux client is still a little immature, and I'm experiencing some problems with it which I'm still trying to work out.  (See my thread here: [http://ubuntuforums.org/showthread.php?t=2097922](http://ubuntuforums.org/showthread.php?t=2097922))

On the server side of my new XMPP network, I am looking at deploying OpenFire.  I currently have OpenFire up and running on my test server, and it seems like a fantastic server for XMPP, however I am not sure how well it will scale, since I'm under 5 users on my test server currently.

What I would love to get out of this thread, is the words of experienced users of Jabber\XMPP using Windows and\or Linux clients for these multimedia features.  What clients are working for you?

I would also enjoy hearing from administrators of XMPP networks, what server solutions are working for you and with how many users?

I hope to get some good feedback!

Thanks
Kirk

---

### Post by rrnbtter on 2012-12-25
Greetings,
I don't use Windows anymore but have been through quite a few Linux chat programs. The one that I find to work the best and to be the easiest to setup is Gajim. It is available for just about all Linux distributions and Windows.  It will autotrade encryption certificates between terminals.  Plenty of features including Video.  Supports XMPP/Jabber and the rest.  Worth a try.

---

### Post by Kirk Schnable on 2012-12-25
> **rrnbtter said:**
> Greetings,
I don't use Windows anymore but have been through quite a few Linux chat programs. The one that I find to work the best and to be the easiest to setup is Gajim. It is available for just about all Linux distributions and Windows.  It will autotrade encryption certificates between terminals.  Plenty of features including Video.  Supports XMPP/Jabber and the rest.  Worth a try.

I will try out Gajim as well, looks promising. Thanks for the suggestion.

---

