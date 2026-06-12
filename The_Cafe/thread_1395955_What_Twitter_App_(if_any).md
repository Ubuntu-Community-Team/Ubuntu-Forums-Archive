---
title: "What Twitter App (if any)"
date: 2010-02-01
forum: The Cafe
---

### Post by HomoGleek on 2010-02-01
What app are you using for twitter? Im using [BuzzBird]("http://getbuzzbire.com") at the mo, although I still from time to time use [TweetDeck]("https://tweetdeck.com/")

---

### Post by speedwell68 on 2010-02-01
Echofon.

---

### Post by juancarlospaco on 2010-02-01
*I use a Bash Identi.ca client, if apply to this discussion.*

---

### Post by Tristam Green on 2010-02-01
[www.twitter.com](www.twitter.com)

hurhurr

---

### Post by ticopelp on 2010-02-01
When I was using Twitter, I used Tweetdeck. Although Spaz was decent.

---

### Post by samantha_ on 2010-02-01
tweetie

---

### Post by aaaantoine on 2010-02-01
I installed Choqok... Though I think in the case of Twitter I would rather...

1. Set up a bash command like juancarlospaco is using for identi.ca, so I can just pull down the terminal and type my thoughts in a single command.
2. Just go to the web site.

Having a native app loaded *just* for tweets is all kinds of silly.  Currently I can read tweets via Akregator (RSS) which is reading from other sources as well.

Though... Admittedly I am intrigued by Choqok's ability to automatically shorten URLs using third party services.

---

### Post by HappinessNow on 2010-02-01
none...Spaz is nice.

---

### Post by juancarlospaco on 2010-02-01
> **aaaantoine said:**
> 
1. Set up a bash command like juancarlospaco is using for identi.ca, so I can just pull down the terminal and type my thoughts in a single command.


Nice to be used with Tilda.[apt:/tilda]("apt:/tilda") :)

---

### Post by aaaantoine on 2010-02-01
> **juancarlospaco said:**
> Nice to be used with Tilda.[apt:/tilda]("apt:/tilda") :)

Precisely.  Though I'm using Yaquake, it's the same idea.

I just set this up now and it works well, though it could use some refinement. (Source and further instructions [here](http://beginlinux.com/blog/2009/07/create-a-twitter-info-server-with-bash/))

```
#!/bin/bash
# tweet_com.sh Tweet from the command line

USERNAME="myusername"
PASSWORD="somepassword"

URL=http://twitter.com/statuses/update.xml
# Post to Twitter with password.
#curl -u $USERNAME:$PASSWORD $URL -d status="$1" | grep truncated

# This asks for the password each time instead.
# Use this if you don't want your password stored in the script.
curl -u $USERNAME $URL -d status="$1" | grep truncated

exit 0
```

I have this script in my home directory and then put this in to set it up...
```
$ chmod +x tweet_com.sh
$ alias tw="~/tweet_com.sh"
```

And finally, an example.

```
$ tw "Hey, I'm postin' to Twitter!"
Enter host password for user 'myusername':
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
104  2057  102  2057    0    33   3805     61 --:--:-- --:--:-- --:--:--  5849
  <truncated>false</truncated>

```

---

### Post by t0p on 2010-02-01
I don't use any app other than my web browser when using Twitter or identi.ca from my computer.  When I'm out and about and want to update my status or whatever, I've got a couple of j2me apps for my cellphone - [MobiTwitter]("http://www.brothersoft.com/mobile/mobi-twitter-11212.html") and [Mobidentica]("http://www.substanceofcode.com/software/mobidentica/") ([which is open source]("http://www.substanceofcode.com/2009/03/24/learning-the-git-mobidentica-now-open-source/")).  I've also got Facebook Mobile, for updating my Facebook status.

As you should have realised from my comments above, I haven't settled on one micro-blogging service yet.  Twitter or identi.ca: which is the best?  Twitter's more popular (I believe) but identi.ca is more popular among Free/open source folk (I've been told).  So what do folk here think?  Which (if any) do **you** use?  Why?  Which should **I** use?  Why?

---

### Post by TheNessus on 2010-02-01
Twitux. nice simple and slim.

---

### Post by Keyper7 on 2010-02-01
Gwibber. The Karmic version is very, very buggy, but the integration with the notify-osd the indicator-applet is neat.

---

### Post by arnab_das on 2010-02-01
seesmic works fine for me.

---

### Post by Resu on 2010-02-01
Pino.

---

### Post by t0p on 2010-02-01
Any particular reason why no one's providing links for their Twitter apps?  Meanness?  Laziness?  Maybe y'all don't want anyone else to use your favourite apps, *Hmmm*?

:p

---

### Post by arnab_das on 2010-02-01
its like if someone wants to use our fav apps, they should do the hard work and do the googling! :P

(or is googling a taboo on ubuntuforums right now? okay how about Yahooing? Google booo, Yahoo yeah! :D right? ) :P

---

