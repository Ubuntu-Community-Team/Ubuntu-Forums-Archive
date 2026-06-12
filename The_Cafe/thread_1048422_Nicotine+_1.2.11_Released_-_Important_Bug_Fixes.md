---
title: "Nicotine+ 1.2.11 Released - Important Bug Fixes"
date: 2009-01-23
forum: The Cafe
---

### Post by OffHand on 2009-01-23
The N+ team released a new version which [fixes]("http://www.nicotine-plus.org/ticket/284") the lock ups people were [experiencing]("http://ubuntuforums.org/showthread.php?t=1025732") if they used too generic search terms.

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)


RELEASE POSTPONED!!

---

### Post by OffHand on 2009-01-24
bump

---

### Post by Eisenwinter on 2009-01-24
I was just in the website, and saw 1.2.11 was released, so I was going to announce it here, but you beat me to it :P

---

### Post by bregnernice on 2009-02-03
Hello.

I love Nicotine Plus :) I would like to update from version 1.2.9. I want all nicotine's awesomeness without the random crashing.

I'm amateur at linux and after reading other posts about how to update im still at a loss how to do it... 

Is it possible to update to newer version and still keep same username, password, info etc. ?

running intrepid x86_64...

---

### Post by kk0sse54 on 2009-02-03
> **bregnernice said:**
> Hello.

I love Nicotine Plus :) I would like to update from version 1.2.9. I want all nicotine's awesomeness without the random crashing.

I'm amateur at linux and after reading other posts about how to update im still at a loss how to do it... 

Is it possible to update to newer version and still keep same username, password, info etc. ?

running intrepid x86_64...

Don't use the one from the Ubuntu repos download it directly from the nicotine+ site or get the latest from svn.

---

### Post by bregnernice on 2009-02-03
OK cool. So I can just install the newer version on top of my current version? And I won't loose my personal info?

Ill try it out...

---

### Post by Eisenwinter on 2009-02-04
No, you won't lose the settings.

Get the one from the website, extract the archive with the **tar** command:
```
tar xvf nicotine<tab_here_to_complete_name>
```

Then to run it, you **cd** into the directory created by the extraction of the archive, and type:
```
./nicotine
```

Of course, you don't want to run it from terminal - so you can create yourself an icon on the top panel (I assume you use Ubuntu with GNOME), and give it a command:
```
~/nicotine_directory/nicotine
```

Then, remove the old version with **apt-get**:
```
sudo apt-get remove nicotine
```

Hope this helped you.

---

### Post by bregnernice on 2009-02-04
I'm running into some problems...

Extracted and installed nicotine+-1.2.10 to my home folder and deleted old version with succes. So now i have a folder called:

/home/my_user_name/nicotine+-1.2.10

Now i want a launcher in my panel so i run the command:

~/nicotine+-1.2.10/nicotine

Now nicotine launches and i get this message in terminal:

'Your X can handle RGBA, but your window manager cannot. Not enabling transparancy.'

Anyways this adds no launcher in panel...

In nicotine it reads:

'Loading plugin handler
It appears '/home/my_user_name/.nicotine/plugins' is not a directory, not loading plugins.'

In addition to this none of my downloads or uploads in list starts and nicotine states that none of the buddy's in my list exist :(

I have changed to new server 'server.slsknet.org:2242' as it asked me to do...

And what is this about?:

[July 17 2008] version NS 13 fixes some major issues with the client's search engine and updates obsolete UPnP functionality. updating is *HIGHLY* recommended to improve the network's overall search functionality and peer to peer connectivity. we expect this to become a mandatory update sometime soon. see the changelog on the download page at [www.slsknet.org](www.slsknet.org) for more details. 

Thought i had just updated..

Sorry for ruining this post with my absolute beginners questions/problems.

Edit: I now realize i'm posting in the wrong subforum... I don't want my boring problems with nicotine+ to make anyones afternoon cup'o tea taste bad so on another note heres a link worth checking out, astronomy picture of the day :) [http://antwrp.gsfc.nasa.gov/apod/astropix.html](http://antwrp.gsfc.nasa.gov/apod/astropix.html)

Still, any help much appreciated

---

### Post by Eisenwinter on 2009-02-04
> 
Now nicotine launches and i get this message in terminal:

'Your X can handle RGBA, but your window manager cannot. Not enabling transparancy.'

About this one, I'm not so sure, I assume you use Ubuntu with GNOME, and are therefore using Metacity.

> In nicotine it reads:

'Loading plugin handler
It appears '/home/my_user_name/.nicotine/plugins' is not a directory, not loading plugins.'
This isn't a problem.
Just create a directory in your ~/.nicotine called "plugins". You don't have to do this if you don't want to.

> In addition to this none of my downloads or uploads in list starts and nicotine states that none of the buddy's in my list exist :(
Check your shares configuration, make sure it's the same directories.

About the buddy list, I'm not so sure, maybe OffHand can give a better answer.
I suppose you can find the buddy list in ~/.nicotine somewhere, look around there, and edit it to your liking if you do find it.

> And what is this about?:

[July 17 2008] version NS 13 fixes some major issues with the client's search engine and updates obsolete UPnP functionality. updating is *HIGHLY* recommended to improve the network's overall search functionality and peer to peer connectivity. we expect this to become a mandatory update sometime soon. see the changelog on the download page at [www.slsknet.org](www.slsknet.org) for more details. 

Thought i had just updated..
That message has nothing to do with Nicotine+ itself, it's intended for the users of the official Soulseek client, which is made only for Windows.

Since you **are** connected to the Soulseek server, you also get this message in Nicotine+.

---

### Post by bregnernice on 2009-02-04
Ill end my post here on a positive note: Nicotine is updated succesfully. Thanks a million!

The problem seemes to be this: 

 WARNING: You are connected to the old server, which will most likely be shut down in the near future. To connect to the new Soulseek server edit your settings and change the server port from 2240 to 2242

When i change to port 2242 nothing works so im back to using port 2240 and everything is downloading fine again, searching works and buddy list online:)

Cheers

---

### Post by OffHand on 2009-02-04
> **bregnernice said:**
> Ill end my post here on a positive note: Nicotine is updated succesfully. Thanks a million!

The problem seemes to be this: 

 WARNING: You are connected to the old server, which will most likely be shut down in the near future. To connect to the new Soulseek server edit your settings and change the server port from 2240 to 2242

When i change to port 2242 nothing works so im back to using port 2240 and everything is downloading fine again, searching works and buddy list online:)

Cheers

I can really recommend downloading the subversion version:

```
svn checkout http://nicotine-plus.org/svn/trunk/nicotine+ nicotine+
```

This will create a nicotine+ directory in your home folder. Pretty much the same as downloading the tar and extracting it, but you can easily update it with:
```
svn up
``` command.

Click [here ]("http://www.nicotine-plus.org/wiki/NicotineFromSubversion")for more information about subversion.

---

### Post by OffHand on 2009-02-04
> **bregnernice said:**
> I'm running into some problems...

Extracted and installed nicotine+-1.2.10 to my home folder and deleted old version with succes. So now i have a folder called:

/home/my_user_name/nicotine+-1.2.10

Now i want a launcher in my panel so i run the command:

~/nicotine+-1.2.10/nicotine

Now nicotine launches and i get this message in terminal:

'Your X can handle RGBA, but your window manager cannot. Not enabling transparancy.' Should be fixed in svn. Try to use full path instead of ~/

> **bregnernice said:**
> 
In nicotine it reads:

'Loading plugin handler
It appears '/home/my_user_name/.nicotine/plugins' is not a directory, not loading plugins.' what the previous poster said. Plugins are experimental atm.

> **bregnernice said:**
> 
In addition to this none of my downloads or uploads in list starts and nicotine states that none of the buddy's in my list exist :( That sucks. Send me a tell on N+ and we can try to sort out the down- and uploads. The buddies excist on the old server. They did not change to the new server yet. Out of our control.

> **bregnernice said:**
> 
And what is this about?:

[July 17 2008] version NS 13 fixes some major issues with the client's search engine and updates obsolete UPnP functionality. updating is *HIGHLY* recommended to improve the network's overall search functionality and peer to peer connectivity. we expect this to become a mandatory update sometime soon. see the changelog on the download page at [www.slsknet.org](www.slsknet.org) for more details. 

Thought i had just updated.. That message is for Soulseek.exe users. You can ignore that. It's sent by the server.

> **bregnernice said:**
> 
Sorry for ruining this post with my absolute beginners questions/problems. We all had to learn it. No worries.

> **bregnernice said:**
> 
Edit: I now realize i'm posting in the wrong subforum... I don't want my boring problems with nicotine+ to make anyones afternoon cup'o tea taste bad so on another note heres a link worth checking out, astronomy picture of the day :) [http://antwrp.gsfc.nasa.gov/apod/astropix.html](http://antwrp.gsfc.nasa.gov/apod/astropix.html)

Still, any help much appreciated

---

### Post by Bakon Jarser on 2009-02-09
It says 1.2.11 has been delayed.  I upgraded to the svn version (1.2.12svn).  The upgrade went smoothly and all of my settings are still there.

---

### Post by OffHand on 2009-02-10
> **Bakon Jarser said:**
> It says 1.2.11 has been delayed.  I upgraded to the svn version (1.2.12svn).  The upgrade went smoothly and all of my settings are still there.

Good to hear. I always recommend using svn anyways because it is usually stable enough to use every day.

---

### Post by basscad on 2009-02-13
> **bregnernice said:**
> 

When i change to port 2242 nothing works so im back to using port 2240 and everything is downloading fine again, searching works and buddy list online:)

Cheers

ure trying to connect to a different server so:

a. someone may be already using ur username with a different password. try to login with a new username

b. u will lose ur buddy list. and ur old buddys may be using different usernames (if they are on this server at all)

c. u will lose ur current queued lists...

i would recommend the NEW soulseek server though cos it gives u much more results

---

### Post by stylishkoala on 2009-10-04
I have a problem, recently upgraded to Nicotine+ 1.2.12 and by default uses port 2242 to connect and my friends appear logged off because don't exist in that server, when I change to port 2240 (old server) and restart my nicotine+ the port connected is 2242 again :(

Can anyone point me to set by default port 2240 until my buddies change to new servers?

---

### Post by OffHand on 2009-10-04
> **stylishkoala said:**
> I have a problem, recently upgraded to Nicotine+ 1.2.12 and by default uses port 2242 to connect and my friends appear logged off because don't exist in that server, when I change to port 2240 (old server) and restart my nicotine+ the port connected is 2242 again :(

Can anyone point me to set by default port 2240 until my buddies change to new servers?

Settings > Server >Manually change the 2 to a 0  :popcorn:

p.s. From 1.2.13 upwards you can select it with dropdown menu.

p.s. I just woke up and did not read your post properly. Go into the .nicotine folder and edit the config file manually.

---

