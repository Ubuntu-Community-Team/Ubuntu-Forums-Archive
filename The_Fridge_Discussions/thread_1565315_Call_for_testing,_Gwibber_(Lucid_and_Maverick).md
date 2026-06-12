---
title: "Call for testing, Gwibber (Lucid and Maverick)"
date: 2010-08-31
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-08-31
[IMG]http://fridge.ubuntu.com/files/Gwibber.192x192.png[/IMG]
Today is the day affectionately known as &#8220;Twitter&#8217;s OAuthpocalypse&#8221;. Twitter is shutting down basic auth completely, which Gwibber has relied on.  So after today Twitter will cease to work for anyone that hasn&#8217;t updated to the OAuth enabled version of Gwibber.  I have uploaded packages for both Maverick and Lucid to the ~ubuntu-desktop PPA for testing.  We need to get an SRU out pretty quickly for Lucid.

 Any testing would be greatly appreciated, please provide feedback on this list.

 [https://edge.launchpad.net/~ubuntu-desktop/+archive/ppa](https://edge.launchpad.net/~ubuntu-desktop/+archive/ppa)

 Make sure you restart gwibber-service, you should be prompted to authorize Twitter.

 Originally sent to the [ubuntu-desktop mailing list]("https://lists.ubuntu.com/archives/ubuntu-desktop/2010-August/002626.html") on Tue Aug 31 2010

 

[More...](http://fridge.ubuntu.com/node/2116)

---

### Post by Vinze on 2010-08-31
I'm not going to subscribe to the ubuntu-desktop mailinglist just to say this, so I hope you can read it here :)

The problem with the current implementation is that it completely disregards the advantage of OAuth, namely, that the user does not have to trust the application to not steal his/her password. For proper OAuth support, I suppose the browser should be opened with the correct URL (which I'll admit is not ideal) that the user can check.

Apart from that, it worked fine, except that I wasn't prompted to authenticate but had to manually open the accounts dialog. If more info is needed I suppose you'd need to send a PM as I'd get an email notification for that. Or allow me to report bugs somewhere ;)

---

### Post by Grone1985 on 2010-09-01
Hi! I'm running Lucid x32 and Twitter works fine... On the other hand Facebook doesn't work anymore, I can't authorize the account, when I type my info as requested it says that Gwibber had a problem and that I should try again later. Any help with that? Thanks!

---

### Post by fluteflute on 2010-09-01
> **Vinze said:**
> I'm not going to subscribe to the ubuntu-desktop mailinglist just to say this, so I hope you can read it here :)

The problem with the current implementation is that it completely disregards the advantage of OAuth, namely, that the user does not have to trust the application to not steal his/her password. For proper OAuth support, I suppose the browser should be opened with the correct URL (which I'll admit is not ideal) that the user can check.

Apart from that, it worked fine, except that I wasn't prompted to authenticate but had to manually open the accounts dialog. If more info is needed I suppose you'd need to send a PM as I'd get an email notification for that. Or allow me to report bugs somewhere ;)
Bug filed: [https://bugs.edge.launchpad.net/gwibber/+bug/627871](https://bugs.edge.launchpad.net/gwibber/+bug/627871)

---

### Post by jjvenkit@uwaterloo.ca on 2010-09-01
Is there any reason to use the ppa:ubuntu-desktop/ppa versions of gwibber (2.31.91~bzr813-0ubuntu1 and 2.30.2~bzr742-0ubuntu1) instead of the ppa:gwibber-daily/ppa version (2.31.91~bzr833-0ubuntu1~daily1)?

jason.

---

### Post by kenvandine on 2010-09-01
At the time the oauth branch hadn't been merged yet, so the dailies didn't have that change.  It should now.  Also the dailies only helps test trunk, which is very different than what is in Lucid, and we do need testing for the stable release as well.

---

### Post by Joshua Lückers on 2010-09-01
First launch after the update showed 5 "Broadcast Account" dialogs.
After closing them all and restarting Gwibber the dialog did not reappear and had to open it manually. 
Furthermore it works fine.

---

### Post by kenvandine on 2010-09-01
> **Grone1985 said:**
> Hi! I'm running Lucid x32 and Twitter works fine... On the other hand Facebook doesn't work anymore, I can't authorize the account, when I type my info as requested it says that Gwibber had a problem and that I should try again later. Any help with that? Thanks!
The facebook problem is a separate issue, and not new unfortunately.  That is facebook throttling Gwibber users.  They allocate a number of requests per day on an application level, not user.  So Gwibber is frequently over that allocation, which means they reject all users requests not just the ones that are over over the allocation.  We are trying to find a good solution and have already optimised our requests as much as we think.  We may need to start tracking how aggressive users are and limit it in the client, which would be quite a bit of work.  Basically when you use up your own fair share of the allocation, we prevent gwibber from making more requests until the next day.  

Anyway we look at it, it isn't great.

---

### Post by kenvandine on 2010-09-01
> **fluteflute said:**
> Bug filed: [https://bugs.edge.launchpad.net/gwibber/+bug/627871](https://bugs.edge.launchpad.net/gwibber/+bug/627871)
The advantage of OAuth is the password isn't stored locally in the application, the authorization is managed by the web service and the client application just stores the key provided by the service.  If a user revokes it with the web service, the client can't use it.

---

### Post by ernstp on 2010-09-01
I missed the small save-button in the account preferences and thought I had found a bug first. It's not very obvious that you have to save first.

---

### Post by jjvenkit@uwaterloo.ca on 2010-09-01
The lucid version (2.30.2~bzr742-0ubuntu1) seems to work fine but I had to manually kill the pre-existing gwibber-service in order to get gwibber-2.30.2~bzr742-0ubuntu1 to start up and ask me to re-authenticate my twitter account.

Ernstp at comment#10 ([http://ubuntuforums.org/showpost.php?p=9793708&postcount=10](http://ubuntuforums.org/showpost.php?p=9793708&postcount=10)) is right that the save button is poorly placed.  Does there have to be a save button at all?  If the twitter response is positive then shouldn't that be enough?

Also the entire twitter login screen didn't fit into the gwibber window I had open.  About 1/3, the portion with the twitter terms, was cut-off.  I had to stretch the window to see it. I would have though that the gwibber window would stretch to fit the data from twitter instead of using a scrollbar.

As an aside, I wish the ability to do twitter groups would find its way down into the stock lucid version of gwibber.

---

### Post by zeroseven0183 on 2010-09-02
Twitter is now working in version 2.30.2~bzr742.
So far, so good!

---

### Post by Rainfly_X on 2010-09-03
The update mostly works for me, but I have two different Twitter accounts, and I can only use one at a time (the one I've most recently authorized). Ironically, I actually need to be able to use both right now *because *of the recent OAuth incident, so for the moment I have my main account open in the browser, and my special account open in Gwibber. I'd really like to figure out how to get both of them to work, but it feels like an under-the-surface kind of bug to me, and I'd rather not dive into the source code and then have someone experienced fix it before I can figure it out anyways.

---

### Post by Rainfly_X on 2010-09-03
Sorry for the double-post, not sure how to edit. But multi-account is working now, and I'm not sure what was buggering it up before. So false alarm, sorry.

---

### Post by stone1343 on 2010-09-08
I'm not using the PPA version of Gwibber, but on both Maverick and Lucid, the OAuth dialog was in French for me. See attachments. What package would that bug be against?

---

