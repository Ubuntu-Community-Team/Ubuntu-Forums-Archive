---
title: "Transfering sensitive data quickly and securely?"
date: 2011-06-27
forum: Security
---

### Post by NormaJean on 2011-06-27
Ahoy hoy, 

Just wanting to bounce around ideas with people who know more about this then me ;) 
My company needs to send sensitive data across to another company, 800gb of .dpx.

The way I have thought of is:
E-Sata/1TB WD black. 
True-encrypted/ hw accelerated aes (3x machines being built with 2600k) 
Sha1sum on each file. 

The main goal is to make sure that 
1. The files that were transferred off the server onto the drive, are exactly the same. 
2. Secure. 
3. Fast. 

Thanks in advanced!

---

### Post by papibe on 2011-06-27
I'll assume that the machines are running Linux. I would: [LIST]
[*]Create non admin accounts.
[*]Disable shell and login using passwords.
[*]Create ssh keys for secure logins.
[*]Transfer files using rsync over ssh using the encrytion option.
[/LIST]

Just a thought.

---

### Post by NormaJean on 2011-06-27
They will need to be sent by DAS due to various constraints of our connections.
Sorry, I should have specified.

-----
Also, the systems are there because we will be sending over 50 of these drives out.

---

### Post by drdos2006 on 2011-06-28
Sounds to me like you need to set up VPN and let the 50 clients download from your server.
my 2cents worth.

regards

[edit]
Maybe if you have limited upload, then upload to another server with a big download pipe....then allow downloads from there. You did not specify the limitations of your connections. Maybe a torrent might be more suitable.???
[/edit]

---

### Post by NormaJean on 2011-06-28
We're a production house, you mention the word torrent and everyone leaps.
I'm not sure the exact specifics of the connection at our D/C, something to find out -- I was just told that when they investigated the idea of having them just download off us that 800gb- 2TB from 50 different companies is too much of an ask. 

Which is fair enough, but cheers for the input it is something that I will be investigating.

---

### Post by Drenriza on 2011-06-28
If you send data on a regular basis, then why not use a internet connection with a site-to-site or secure GRE tunnel over a VPN connection?

Use isakmp, defi helman group 1, 2 or 5, with an AES 128, 192 or 256 encryption to exchange keys and use a AES 128, 192 or 256 encryption, with a hash value with ipsec for the data transfer.

And control the data transfer with a access control list.
To control who can download and who cant, what data should be encrypted, and so on. Make a access-list that allows different clients to download at different times. The sky is the limit :p

EDIT.
And with low lifetimes on (key exchange, transfer set, tunnel validation) to keep everything secure.

---

### Post by SeijiSensei on 2011-06-28
> **NormaJean said:**
> We're a production house, you mention the word torrent and everyone leaps.

Sad to hear that.  A situation where you're shipping a single large file to 50 clients is an ideal case for torrenting.  Perhaps your staff needs a little education on the difference between a protocol like bittorrent and what people do with it.  You might remind them that people transfer illegal files lots of other ways, too.  Even by good-old HTTP.

Oh, and most torrent clients include an encryption option for an additional layer of security.

---

### Post by Lars Noodén on 2011-06-28
> **NormaJean said:**
> They will need to be sent by DAS ...

What is DAS?

---

### Post by HermanAB on 2011-06-28
You mean: Was ist DAS?
;)

Anyhoo, the OP mentioned a HW encrypted HDD.  That is certainly a good way to do it.  Just copy the data with rsync onto the disk.  Rsync has error detection built in, so the copy will be good.  Then send the disk with a courier.

---

### Post by Bachstelze on 2011-06-28
1. Make a big .tar with all the files, compute SHA512 checksum of the .tar
2. Encrypt with GnuPG, send the key and checksum through SSH since it's small
3. Copy on the drive, no need for TrueCrypt since it's already encrypted
4. Ship drive
5. Let them decrypt it and verify the checksum
6. Profit

---

### Post by NormaJean on 2011-06-28
**SeijiSensei**: We know, but sadly everything we do (storage team) is heavily influenced by what they think they need. So even though it's not the most viable -- essentially, what they say goes. 

**Lars Noodén**: Direct Attached Storage, external drive.

**HermanAB**: I totally forgot about rsync /doh. Will give it a performance run. 

**Bachstelze**: Cheers, The way we were going to have it is have 1gb of unencrypted with a txt of the checksum but I like the idea of them ssh'ing into a box and just grabbing the file. 

Thanks guys, I'll let you know how we go in the next month or so.

---

