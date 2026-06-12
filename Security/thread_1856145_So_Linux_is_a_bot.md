---
title: "So Linux is a bot?"
date: 2011-10-07
forum: Security
---

### Post by Guitar John on 2011-10-07
I got an e-mail yesterday from my ISP that my computer is infected with a bot.  Please click on the provided link for a solution.  I dismissed it as a phishing scam and deleted the message.

Today, they called my cell phone, leaving a similarly ominous voice-mail message.

So what gives?  Are they seeing Linux on all of my computers and, unable to comprehend something that is not Windows, assuming it is spyware?  Or is there really something to this?

---

### Post by matt_symes on 2011-10-07
Hi

Have you asked your ISP why they think you have a bot ? Ask them to elucidate this. Please post back their response.

Incidentally, answer your phone ;)

Kind regards

---

### Post by Dangertux on 2011-10-07
Usually when ISP's send those types of notifications it's not because of your operating system. It's because they notice traffic on a certain port frequented by malware. Are you running any servics on oddball ports?

If not you might want to verify their claims, and reasoning for this. They may be seeing something that you can't.

---

### Post by OpSecShellshock on 2011-10-07
Perhaps you can help each other. They can tell you why they think you have a bot, and you can explain to them that it's poor form asking you to follow a link in an email.

---

### Post by HermanAB on 2011-10-09
Run Wireshark and look at the network traffic.  If you are running servers like FTP, Apache or VNC, then your machine may very well be infected with a bot.

---

### Post by mikewhatever on 2011-10-09
Perhaps one of your computers is infected. It's not unheard of.

---

### Post by The Cog on 2011-10-09
I agree that you should ask them why they think you have a bot - what ports/protocols or network traffic have they seen being used from your computer that makes them think that? Knowing the port number will help you track it down locally.

---

