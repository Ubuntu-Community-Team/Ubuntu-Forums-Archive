---
title: "Airmon-ng error: No matching network found - check your bssid"
date: 2013-07-07
forum: Security
---

### Post by enduser79 on 2013-07-07
I'm using Aircrack to experiment with my Cisco test network at home.


[B]SSID = ccna-wireless

Channel = 6

AP MAC = 00:15:C7:FD:60:B0

Target machine MAC = 24:77:03:A0:06:6C

Encryption type = WPA2

Authentication = PSK[/B]

Everything seems to work just fine, I first use inSSIDer in Windows to locate the target SSID, MAC address and channel.

I then capture the handshake (this shot was taken afterwards, so you won't see the handshake, but it was there)

[IMG]http://i993.photobucket.com/albums/af51/norcalecm/airmon-nghandshake_zpsedc56975.png[/IMG]



The deauthentication works fine as well....

[IMG]http://i993.photobucket.com/albums/af51/norcalecm/airmon-ngdeauth_zpsdb4068c5.png[/IMG]


I then try to crack, but get an error.....

[IMG]http://i993.photobucket.com/albums/af51/norcalecm/airmon-ngerror_zps5b8f344b.png[/IMG]


Can someone please point me in the right direction of why it isn't working. Do I need to capture more packets? (first screen shot, under data)

I'm also interested in being able to use other password lists.....

Thanks.

---

### Post by enduser79 on 2013-07-07
Ok, I figured what happened, but I do get another error.  The file I wrote to is called PSK, not output.

I do get an error that the program can't find the dictionary, located in the file password.lst

That does not make sense, since the file is present....

[IMG]http://i993.photobucket.com/albums/af51/norcalecm/airmonnosuchfileordirectory_zps79f9ba1b.png[/IMG]

---

### Post by Irihapeti on 2013-07-07
We don't support aircrack on these forums, even though it's in the repositories. Aircrack has its own forums and you may be able to get help there.

Thread closed.

---

