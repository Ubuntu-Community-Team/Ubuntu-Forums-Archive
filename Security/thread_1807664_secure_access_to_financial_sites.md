---
title: "secure access to financial sites"
date: 2011-07-19
forum: Security
---

### Post by Advait on 2011-07-19
Hi All,

I'm using Ubuntu 10.10. The main reason I'm using Ubuntu is that I feel it"s much safer for accessing my financial sites than my 64 bit Windows 7. For added security in my Ubuntu I'm using Firefox with NoScript running. And I'm using LastPass Premium with the Yubiky (that way I never have to type in my user names and passwords for my financial sites).

Is there anything else I should be doing in Ubuntu to increase the security of my access to my financial sites?

I plan to upgrade to 11.04 as soon as I can confirm that 11.04 works with my Reliance cellular modem USB device (I live in India).

Thanks! I love the Ubuntu forums.

Tom

PS: I've actually done a lot to try and really harden my Windows 7 system. I've listened to all the Steve Gibson "Security Now" episodes and implemented many of their recommendations. But from all that I've heard Ubuntu is still much safer.

---

### Post by bodhi.zazen on 2011-07-19
Financial transactions involve 3 or 4 factors, depending on how you  count them.

1/2 - your OS and your browser. Ubuntu is by default more secure then windows and firefox is more secure then IE. However, firefox has vulnerabilities so it helps to secure firefox

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

And confine firefox with apparmor.

3. "The internet" - this comes down to use https ;)

4. The security of your financial institutions servers, as recent hacks have demonstrated.

---

### Post by Dangertux on 2011-07-19
> **bodhi.zazen said:**
> 
3. "The internet" - this comes down to use https ;)


In my opinion -- this is where you should be spending most of your time. You noted you have a cellular Internet provider.

That's terribly convenient but dependent on your providers standards not necessarily the most secure thing in the world. 

I absolutely agree that you need to make sure your financial institution (and your system) utilize end to end encryption via SSL or TLS. Also in my opinion you need to be getting with your cellular provider and finding out what type of encryption their network offers. Cellular encryption methods work very differently. Consider this, if your Cellular provider is not taking care of their end of the deal , data could be spewed off of a tower unencrypted. This is why it is important to understand their encryption methodology and reinforce it with HTTPS encryption. 3G and 4G encryption methods(namely A5/1 and A5/3 are not particularly secure.)

---

### Post by Advait on 2011-08-27
You're very correct. I always make sure https is on when I go to financial web sites. Without https I'm a sitting duck! :-)

> **Dangertux said:**
> In my opinion -- this is where you should be spending most of your time. You noted you have a cellular Internet provider.

That's terribly convenient but dependent on your providers standards not necessarily the most secure thing in the world. 

I absolutely agree that you need to make sure your financial institution (and your system) utilize end to end encryption via SSL or TLS. Also in my opinion you need to be getting with your cellular provider and finding out what type of encryption their network offers. Cellular encryption methods work very differently. Consider this, if your Cellular provider is not taking care of their end of the deal , data could be spewed off of a tower unencrypted. This is why it is important to understand their encryption methodology and reinforce it with HTTPS encryption. 3G and 4G encryption methods(namely A5/1 and A5/3 are not particularly secure.)

---

