---
title: "Created Ubuntu SSO, not able to login to AskUbuntu"
date: 2013-12-11
forum: The Cafe
---

### Post by DigitalGrinch on 2013-12-11
Supposedly we only need one single login to access all of Ubuntu, but when I am already logged in here and go to AskUbuntu.com, it wants me to login.
That should not happen if SSO is working.

On that login page I have some options. I have an Ubuntu SSO login and password, I should not have to sign-in using a 3rd party openID. Using google search I found a page on AskUbuntu said to use the Launchpad openID, as it was the same DB as SSO but had not changed names. This does not work, for me. Probably because I do not have a launchpad.

I tried to go into general settings here to see if I could configure Launchpad openID options as suggested on another post, but I can not do that either, there are restrictions.

So my question is, are there plans/ETA to get SSO working properly, and what should I do to sign-in to AskUbuntu using my SSO login, in the mean time?

---

### Post by coffeecat on 2013-12-11
As this is not an Ubuntu technical support question, I've moved this from the Beginners Section to The Cafe where I am sure someone can answer your question about Askubuntu. Please be aware that askubuntu is separately administered from the forums here.

**Edit**: to pick up this point in your post:

> I tried to go into general settings here to see if I could configure Launchpad openID options as suggested on another post, but I can not do that either, there are restrictions.


The forums have not used Launchpad login since the beginning of the year. Forum login is entirely via Ubuntu One now and the post you found was probably an old one referring to the old method. The restrictions you mention are to do with spam control and are explained in the sticky below. They have nothing to do with login anywhere, Launchpad or Askubuntu.

[http://ubuntuforums.org/showthread.php?t=2034393](http://ubuntuforums.org/showthread.php?t=2034393)

---

### Post by DigitalGrinch on 2013-12-11
Yes, Ubuntu is very clear when registering that profile editing is not an option until 10 posts are made. My question about that was how are we supposed to use AskUbuntu if we can not log in, or change our settings to allow us to login?

---

### Post by CharlesA on 2013-12-11
I must have misunderstood something cuz I can login with my Launchpad info (which is what I used to sign up for StackExchange) to AU.

Of course, that also means I have a launchpad account and use them for OpenID.

---

### Post by DigitalGrinch on 2013-12-11
so SSO does NOT work with AskUbuntu?

---

### Post by CharlesA on 2013-12-12
It's the same thing as Launchpad. They both use OpenID:

> An Ubuntu One account is the new name for what used to be called an Ubuntu SSO account. Your Ubuntu One account is an email address and a password that you use to sign in to Ubuntu services like Ubuntu One Files and Music, Landscape, *Launchpad*, and more.

[https://one.ubuntu.com/help/faq/what-is-an-ubuntu-one-account/](https://one.ubuntu.com/help/faq/what-is-an-ubuntu-one-account/)

You can use launchpad to sign into StackExchange and AskUbuntu.

---

### Post by DigitalGrinch on 2013-12-12
Then why can't I login to launchpad(or AskUbuntu)? I am logged in here through SSO, when I go to launchpad(or AskUbuntu) it wants me to login or create an account.

---

### Post by CharlesA on 2013-12-12
Doesn't it just provide you with a method to have a single set of credentials to log you in, not log you into all sites that support that method of authentication automatically? Just login and be on your way.

---

### Post by philinux on 2013-12-12
I'm logged in here. I go to askubuntu. Choose launchpad enter my user name hit enter and it prefills my details.  Hit enter. Logged in.

No password to enter so it must be using sso.

(Edit me wrong. I was already logged in at launchpad.  Logged out now askubuntu needs launchpad email and password. )

---

### Post by coffeecat on 2013-12-12
> **grinch2 said:**
> Then why can't I login to launchpad(or AskUbuntu)? I am logged in here through SSO, when I go to launchpad(or AskUbuntu) it wants me to login or create an account.

The fact that you are logged in here through Ubuntu One is irrelevant. As I've already mentioned, askubuntu and this forum are separately administered. They are different entities.

There are not many people here who can answer your question definitively since the one askubuntu admin who does frequent this forum from time to time hasn't logged in here for a little while. It's been a long, long time since I created my Launchpad account and I have no difficulty logging into askubuntu using my Launchpad credentials. It looks as though you will have to create a Launchpad account, or log into askubuntu from one of the other several possibilities such as Stack Exchange, myopenID, and so on. Why you can't use Ubuntu One for askubuntu login, I for one don't know. Perhaps they have plans to and haven't implemeted them yet. We've only been using Ubuntu One SSO login here for about 4-5 months.

---

### Post by bapoumba on 2013-12-12
What you have to understand is that Ubuntu SSO gives you one verified identity you can use on several websites of the Ubuntu ecosystem. Thing is, you still have to hit the login button and confirm it is you.

In my univ for ex, I only need to hit the login button when I go from one of its websites to the other.

If you are using browser plugins or extensions that block referral cookies or trackers, it may not work.

Edit : ah sorry, with Launchpad I have to give my password again even though i'm logged into U1.

---

### Post by DigitalGrinch on 2013-12-12
> **CharlesA said:**
> Doesn't it just provide you with a method to  have a single set of credentials to log you in, not log you into all  sites that support that method of authentication automatically? Just  login and be on your way.
The problem is there is no place to  enter a user and password(and bc it is SSO, should not have to). You  can only login through another openID, like launchpad

Phillinux  got it! I had to "login" to launchpad, not using user/pass, just  authenticate through my already logged in SSO. Once I did that I had a  launchpad account/openID. I went back to AskUbuntu, clicked the  launchpad openID and was logged into AskUbuntu as expected.

The  problem is AskUbuntu has no direct openID provided from Ubuntu SSO, it  offers launchpad as openID, but not Ubuntu SSO. The launchpad openID  must be created first, using the Ubuntu SSO, so that Launchpad can be  used to auth to AskUbuntu. Whoever is running the SSO needs to close  this gap.

I feel the fact I am logged into Ubuntu SSO here is completely relevant. 
Ubuntu  SSO claims it allows access to AskUbuntu, as well as these forums and  ubuntu.com. Although they are administered by different people and are  different entities, the login being "SSO" should allow me to access  them, with only signing in once.
 SSO is "a property of [access control]("http://en.wikipedia.org/wiki/Access_control") of multiple related, but independent [software]("http://en.wikipedia.org/wiki/Software") systems. With this property a user [logs in]("http://en.wikipedia.org/wiki/Login")  once and gains access to all systems without being prompted to log in  again at each of them." I should not have to login using the same  credentials on different sites. Once I login to one site, I should be  able to open the others, in the same browser as original SSO login, and  have access.

Bapo is correct, one login, multiple entities in the Ubuntu ecosystem, just need to click login and verify it is you

Thanks to all for the help. Trying to learn etiquette of this forum, I guess I give a "bean" to Phillinux now? Where do I click to do that?

---

### Post by Elfy on 2013-12-12
> Ubuntu SSO claims it allows access to AskUbuntu, as well as these forums and ubuntu.com. 

If that's the case then it needs to be dealt with. Can you tell me where it says that please?

---

### Post by DigitalGrinch on 2013-12-12
You mean where it says Ask Ubuntu should work with SSO? There are lots of places, the first I heard about it was on Ubuntu training material produced by CBT nuggets. As far as official ubuntu.com places, there are a few, an example of which is
[http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/](http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/)

"...This doesn&#8217;t mean that the names of the services will change (e.g. Ask  Ubuntu will continue to be Ask Ubuntu), but the account you use to log  into these services will be your &#8216;Ubuntu One&#8217; account...."
The Ask Ubuntu site is also one of the properties linked from that page that should work with SSO

This is not incorrect, you do not need to "deal" with it. SSO should work with these properties/sites, there are just a few loose ends to tie up. There is a post on AskUbuntu(from 2012) mentioning the future move to UbuntuSSO away from Launchpad, but I guess that still is not completed yet

---

