---
title: "Is hotmail safe? No https access via web"
date: 2010-04-07
forum: The Cafe
---

### Post by e24ohm on 2010-04-07
Folks:
I am not trying to start flame war; however, I needed to use "hotmail" for a microsoft download. I noticed once logged in, that the website does not provide access via HTTPS. The login session does; however, not the website.

I varified this wireshark, and email sent from hotmail, is sent via HTTP, and while working in hotmail web interface, also uses http.

Is this safe? I relize that most email traffic is unencrypted or uses SSL; however, I did notice that gmail provies a SSL, via its web interface.

But my main question is. "is hotmail safe to use"?

Thanks.

---

### Post by juancarlospaco on 2010-04-07
Is safe, i can safely Sniff all your data...

---

### Post by e24ohm on 2010-04-07
Well, yeah but cant you do that with regular email when using outlook or Thunderbird?

---

### Post by themarker0 on 2010-04-07
I've used it for about 7 years, same email, same password. Never had one security issue.

---

### Post by Phrea on 2010-04-07
I think it's fairly safe. Been using it for years, never had any problems.
BTW, it does use HTTPS, only not at web login.

If you just need a valid email address to register somewhere for something, just use [http://10minutemail.com/10MinuteMail](http://10minutemail.com/10MinuteMail)
Maybe not in this case, but it's a good bookmark for future use.

---

### Post by themarker0 on 2010-04-07
> **e24ohm said:**
> Well, yeah but cant you do that with regular email when using outlook or Thunderbird?

Portability.

---

### Post by Druke on 2010-04-07
When looking at the packets in wireshark where you able to see the message being sent?

Authentication isn't an issue if the login is secured (cookies are another issue, and one that I'm not qualified to analyze), so the only "hole" is seeing your incoming and outgoing mail as it is rendered for you.

I think many sites use a system of only securing sensitive data. I suspect that may be the case here.

---

### Post by e24ohm on 2010-04-08
> **Druke said:**
> When looking at the packets in wireshark where you able to see the message being sent?

Authentication isn't an issue if the login is secured (cookies are another issue, and one that I'm not qualified to analyze), so the only "hole" is seeing your incoming and outgoing mail as it is rendered for you.

I think many sites use a system of only securing sensitive data. I suspect that may be the case here.I'm not sure...

---

### Post by blueturtl on 2010-04-08
As long as you store unencrypted text files on someone else's server, they're not really that private anyway. Using https just means that the files are securely transmitted between destinations. If you trust a) the Hotmail staff and b) people who might hack in to hotmail's servers then you're ok.

Note that this applies to any email provider, not just Hotmail.

---

### Post by CharlesA on 2010-04-08
> **blueturtl said:**
> As long as you store unencrypted text files on someone else's server, they're not really that private anyway. Using https just means that the files are securely transmitted between destinations. If you trust a) the Hotmail staff and b) people who might hack in to hotmail's servers then you're ok.

Note that this applies to any email provider, not just Hotmail.

That applies to pretty much anything in "the cloud."

---

### Post by Khakilang on 2010-04-08
One thing for sure I try not to send sensitive or private stuff using any webmail unless I got no choice. Anyway is Facebook safe?

---

### Post by CharlesA on 2010-04-08
> **Koh Kook Loon said:**
> One thing for sure I try not to send sensitive or private stuff using any webmail unless I got no choice. Anyway is Facebook safe?

Is it encrypted?

---

### Post by Khakilang on 2010-04-08
> **CharlesA said:**
> Is it encrypted?

That is one part I haven't learn yet. Definitely will try to use. So much to learn.

---

### Post by suyashpandit on 2010-04-08
ya its safe

---

### Post by dmizer on 2010-04-08
If you're concerned about security, hotmail can be accessed from your favorite email client via SSL. More information here: [http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry)

---

### Post by samalex on 2010-04-08
> **e24ohm said:**
> Folks:
I am not trying to start flame war; however, I needed to use "hotmail" for a microsoft download. I noticed once logged in, that the website does not provide access via HTTPS. The login session does; however, not the website.

I varified this wireshark, and email sent from hotmail, is sent via HTTP, and while working in hotmail web interface, also uses http.

Is this safe? I relize that most email traffic is unencrypted or uses SSL; however, I did notice that gmail provies a SSL, via its web interface.

But my main question is. "is hotmail safe to use"?

Thanks.

Actually it's a common misnomer that the initial login page must be encrypted in cases like this.  The encryption needs to happen when the form is submitted/posted back to the web server from your browser, and this can happen without you seeing HTTPS anyplace.  Most sites do show the initial login as an HTTPS page for your comfort, but it's not required.  

Now once you log-in if your connection is still using HTTP then be advised that that content is being sent in plain text, but the login credentials may have been encrypted.

I just checked the source code behind hotmail.com (which redirected me to login.live.com) and that's exactly what it's doing.  The form submission is using HTTPS so your credentials are encrypted, so no worries there. 

Lots of services will only encrypt the login credentials like this because it cuts back on overhead since SSL connections are much more taxing then standard HTTP connections.  

If I'm using a banking site then I expect that comfort of an initial HTTPS page to be there both before, during, and after logging in, but on other sites I'm not too worried.  Just check the source on the login page if you're paranoid and it'll tell either way.

Sam

---

