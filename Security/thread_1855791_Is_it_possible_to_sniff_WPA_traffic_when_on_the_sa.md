---
title: "Is it possible to sniff WPA traffic when on the same network?"
date: 2011-10-06
forum: Security
---

### Post by KIAaze on 2011-10-06
A simple question about how WPA/WPA2 works:
Is it possible to sniff WPA traffic when on the same network?
i.e. does it encrypt each connection with a separately generated key? Or do all use the same, so that one can decrypt packets from all other connected users?

---

### Post by Dangertux on 2011-10-06
Yes it is possible to sniff WPA/2 traffic so long as you have the key. Note, this is assuming PSK (Pre-Shared Key) method of encryption.

The WPA key is the same for the entire AP. That being said, the key is generated in two parts. Half by the AP and half by the Client. 

When a 4 way handshake is captured, you have all the information needed to crack the key.  However, you must find the passphrase that matches the key. Hence the dictionary method of attack as opposed to the statistical attacks of WEP. However, once you have the key traffic is most certainly sniffable.

If you are concerned about this make sure you are forcing SSL or some other form of end to end encryption.

---

### Post by KIAaze on 2011-10-06
> However, you must find the passphrase that matches the key. 
Isn't that the passphrase used to connect to the network?
> the key is generated in two parts. Half by the AP and half by the Client.
So the traffic of each client has a different encryption key?
But knowing the passphrase of the WPA network, one can easily decrypt it anyway?

(My scenario is quite simple: wireless network shared with multiple people.)

---

### Post by Dangertux on 2011-10-06
The simple answer is yes it can be sniffed if they all have the WPA key.

To elaborate clearly I should not have used the word generated, instead provided.

Part of the key is provided as a challenge (by the AP) the other by the client (response) the two parts together complete the 4 way hand shake, and give you the WPA key.

Since this is not about cracking the network that bit is irrelevant, since they will all be on the same network. So anyone with wireshark or another sniffing utility can capture any and all traffic traversing the network.

---

### Post by KIAaze on 2011-10-06
Ok, thanks.
While I'm at it:
What about cable connections?
Can people connected via cable to the router sniff wireless traffic (without the wireless or router passphrase)? And vice-versa or between cable-connected clients?
And in the case of a simple ethernet switch?

---

### Post by Dangertux on 2011-10-07
Yes but it gets much more complicated at that point. If they are on a switch, with the WAP they can still sniff it but it turns into a man in the middle attack at that point as opposed to just sniffing traffic. Since they are no longer in the path of broadcasted traffic they have to put themselves there. See ARP / DNS poisoning.

---

### Post by KIAaze on 2011-10-07
Ok, thanks.

---

