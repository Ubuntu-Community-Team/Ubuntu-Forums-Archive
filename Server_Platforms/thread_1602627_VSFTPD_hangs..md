---
title: "VSFTPD hangs."
date: 2010-10-21
forum: Server Platforms
---

### Post by sprk on 2010-10-21
Hello!

I'm trying to get a secure vsftpd server running. The problem is that it seems to hang very often, or something. At the moment I'm the only one using it but soon more people will and this problem is very annoying!

When I connect with FileZilla (Sorry for Swedish, I hope you get most of it anyway):

```
Status:    Anslutningen etablerad, väntar på välkomstmeddelande... (Connection established)
Svar:    220 <edited>
Kommando:    AUTH TLS
Svar:    234 Proceed with negotiation.
Status:    Initierar TLS...
Status:    Validerar certifikatet...
Kommando:    USER <edited>
Status:    TLS/SSL-anslutning etablerad.
Svar:    331 Please specify the password.
Kommando:    PASS *************
Fel:    Tidsgränsen för anslutningen överstegs (Time limit exceeded)
Fel:    Kunde inte ansluta till servern (Can't connect)

Status:    Väntar på att försöka igen... (Try again...)
Status:    Slår upp adressen för <edited> (DNS'ing)
Status:    Ansluter till <edited>:21212...
Status:    Anslutningen etablerad, väntar på välkomstmeddelande... (Connection established)
Fel:    Tidsgränsen för anslutningen överstegs (Time limit exceeded)
Fel:    Kunde inte ansluta till servern (Can't connect)

```The only cure I have found is to do a killall -9 vsftpd from a remote console, followed by service vsftpd start. I've tried putting those in cron.hourly but they don't fix it nor will the service vsftpd restart. It only works when I'm logged in and sudo'd. 

Is anyone familiar with this problem?

---

