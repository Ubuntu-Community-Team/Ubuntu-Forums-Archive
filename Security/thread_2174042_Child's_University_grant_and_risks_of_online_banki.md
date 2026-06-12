---
title: "Child's University grant and risks of online banking using Ubuntu 12.04 LTS."
date: 2013-09-12
forum: Security
---

### Post by resander on 2013-09-12
I don't know much about this type of Ubuntu security...

I have been using online banking from a desktop with Ubuntu for our household money since around 2011 and have never had any keystroke loggers hiding, snooping and trying steal our money. From the beginning I have done the online banking from a user account dedicated to this purpose only and have never accessed other websites or email from it. My rationale was that then no keystroke loggers could get in and read and try my passwords while I was doing online banking. Is this assumption correct/sufficient? Always?

Our eldest daughter has received a student loan and student grant for the academic year starting two weeks from now. She is receiving the money into her bank account, a fair amount of money that she will be nibbling at throughout the academic year. If that money was siphoned off by a keystroke logger she would not be able to continue her studies.

We have a spare Dell E6400 laptop and I have been thinking about putting Ubuntu 12.04 LTS onto it and let our daughter use it for academic studies and online banking from different accounts as I am doing for the household money. Is there anything else I should do on the Dell laptop to make it impossible for keystroke loggers to take her money? 

Or would it be better for her to go to the bank branch and do all banking manually (would be very inconvenient since the bank is far away from the campus)?

Would be grateful for advice.

Ken

---

### Post by Polydorus on 2013-09-12
Why not open a new account in her college town and you handle transfers?  That way she can do her banking with a local account and you can handle the transfers, as needed, from the existing account to her new account.

---

### Post by resander on 2013-09-12
Thanks Polydorus,

Most university students in UK apply for loans, typically around £16000 per year. The largest part of the loan (£9000) goes directly to the university from the awarding public organisation Student Finance and covers the annual tuition fee. The rest is paid into the students private current account. Our daughter will receive the remainder £7000 into her student current account with one of the largest high-street banks in UK. The largest (ca £4000) part of the remainder goes to rent of student rooms on/off the campus and must be paid monthly. The remainder (£3000) is for books, travel expenses and day-to-day living.

If she has to do all the banking manually, she can open a second current account with the same bank and transfer £3000 from the remainder account and just keep £4000 for the rent to be paid by montly standing order. She can then nibble away from the second account using the ATM/debit card that comes with that account using ATM machines on or near the campus.

If there is a risk using Ubuntu for my own online banking I will consider stopping it and go back to manual transfers and lose a lot of time and convenience.

What do the experts think of the risks? Or put differently, can keystroke loggers really infiltrate normal Ubuntu user accounts? If so, can users stop it or reduce the risk to near zero?

Ken

---

### Post by ventrical on 2013-09-12
@Ken

From my research of Ubuntu Security over the past few years I conclude it is highly improbable that a Microsoft Windows based keylogger can infect an Ubuntu system of any version after 10.04 (as being that is where I had started my test cases). I have heard of pracitcally no cases of malware or *virus* of any type affecting Ubuntu in this way. That is not to say that Ubuntu cannot be affected. There are always malicous java scripts that can attempt to drop packets to the system but they would have to get through the authentication processes first. 

  You are correct in your assumption that visiting certain webpages will drop  tracking cookies but it is my understanding that  for the tracking cookie to be able to grab relevant data that it needs to be designed for Windows services and processes. Also we cannot expect others to practice monastic internet surfing so there will always be a risk.

I'll check back in on this.

---

### Post by ventrical on 2013-09-12
Here is the conventional wisdom which I tend to agreee with.

[http://ubuntuforums.org/showthread.php?t=1476834&p=9686731#post9686731](http://ubuntuforums.org/showthread.php?t=1476834&p=9686731#post9686731)

---

### Post by MartyBuntu on 2013-09-12
Be wary of doing anything you're concerned with security if you're using a public WiFi.
Never transmit passwords and codes (which are sent in plain-text possibly) if you don't know how to harden your security scheme (such as using a VPN).

---

