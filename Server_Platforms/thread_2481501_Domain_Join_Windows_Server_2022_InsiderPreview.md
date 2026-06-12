---
title: "Domain Join Windows Server 2022 Insider/Preview"
date: 2022-12-01
forum: Server Platforms
---

### Post by seb05mar86 on 2022-12-01
Hi, I have the following problem,

I want to join an Ubuntu Server via realmd/sssd into a MS Windows Active Directory domain.
The domain controller is a Windows Server 2022 Insider.
All packages are installed and configured as far as I know.

The DC and the domain can be resolved and "realm discover" also gives me a reasonable output.
With "realm join" I get this error message
```

adcli: joining domain ad.domain.com failed: Couldn't set password for computer account: Ubuntu$: Message stream modified

```

In the meantime, I have tried several things:

1. DC windows server 2022 without insider/preview &#8594; domain join works without problems
2. "realm join" with the option "--membership-software=samba" &#8594;
```

Password for [DOMAIN\Administrator]:gensec_gse_unwrap: GSS UnWrap failed: A token was invalid: unknown mech-code 0 for mech 1 2 840 113554 1 2 2
Failed to join domain: Failed to set machine spn: Time limit exceeded
Do you have sufficient permissions to create machine accounts?

```
3. I get the same errors with a Debian server &#8594; was to be expected
4. set up a Fedora server. with "realm join --membership-software=samba" &#8594; domain join works without problems

All systems are installed as server, core, minimal, etc (without desktop / GUI) and updated to the current time **Edit: / up to date**.
What else can I try, or can someone explain this behavior to me?

With kind regards

---

### Post by MAFoElffen on 2022-12-02
I saw on the Microsoft Tech Forums, where you found that the problem was that your DC was not updated to it's latest updates, and now this issue is resolved:
[https://techcommunity.microsoft.com/t5/windows-server-insiders/ubuntu-debian-join-active-directory/m-p/3684943](https://techcommunity.microsoft.com/t5/windows-server-insiders/ubuntu-debian-join-active-directory/m-p/3684943)

Please come back and share your solution and mark your thread as Solved.

---

### Post by seb05mar86 on 2022-12-02
It was all DC updated. I have tested it again.

Fedora can connect to the Win Server 2022 Insider/Preview Ubuntu/Debian cannot.

my guess is that something has to do samba / adcli

[TABLE="class: grid, width: 500"]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]fedora 37[/TD]
[TD="align: center"]ubuntu / kinetic[/TD]
[TD="align: center"]new / **old**[/TD]
[/TR]
[TR]
[TD="align: center"]samba[/TD]
[TD="align: center"] 4.17.1 / 19 Okt 2022[/TD]
[TD="align: center"]4.16.4 / 02 Aug 2022[/TD]
[TD="align: center"]4.17.3, 4.16.7 / 15 Nov 2022
**4.16.4 / 27 Jul 2022**[/TD]
[/TR]
[TR]
[TD="align: center"]realmd[/TD]
[TD="align: center"] 0.17.0-11 / 23 Jul 2022[/TD]
[TD="align: center"] 0.17.0-2 / 17 Jun 2022[/TD]
[TD="align: center"]0.17.1 / 29 Sep 2022
**0.17.0 / 19 Feb 2021**[/TD]
[/TR]
[TR]
[TD="align: center"]adcli[/TD]
[TD="align: center"] 0.9.1-11 / 20 Jul 2022[/TD]
[TD="align: center"] 0.9.1-1 / 24 Feb 2022[/TD]
[TD="align: center"]0.9.2 / 28 Sep 2022
**0.9.1 / 20 Feb 2021**[/TD]
[/TR]
[/TABLE]


I find the time periods until Ubuntu updates packages a bit too long.
It's also not easy to find a good way for an update policy.

I would like to see Ubuntu have an update channel like Debian's sid or have a rolling release channel.
Many distributions provide the kernel 6, except Ubuntu.

Theoretically, I could do without a local DC, but Linux doesn't yet offer an AzureAD join for local servers.

I would like to use ubuntu because I think they work more closely with Microsoft than other distributions.

---

### Post by MAFoElffen on 2022-12-03
There was a difference I saw yesterday, between Fedora (RHEL)and Ubuntu (Debian) on joining Domain), that had to do with home directories... Maybe a try. I have to look in my history from yesterday to look it back up.

BRB...

What is the output of 'realm discover'?

---

### Post by MAFoElffen on 2022-12-03
I think this was one of the pages I read yesterday. Not exactly, the one I was looking for but similar. With Fedora, you don't have to do the extra pam step for creation of home directories...
[https://laputer.com/how-to-join-ubuntu-22-04-with-active-directory/](https://laputer.com/how-to-join-ubuntu-22-04-with-active-directory/)

Still looking for the exact page that said that there was a difference. 

These were in my history from yesterday:
[https://www.server-world.info/en/note?os=Ubuntu_22.04&p=realmd](https://www.server-world.info/en/note?os=Ubuntu_22.04&p=realmd)
[https://devopstales.github.io/home/ubuntu-22.04-ad-join/](https://devopstales.github.io/home/ubuntu-22.04-ad-join/)
[https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/)

---

### Post by MAFoElffen on 2022-12-03
> On RHEL based systems, user’s home directory will be created automatically. On Ubuntu / Debian, you need to enable this feature.
from: [https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/)

```

sudo bash -c "cat > /usr/share/pam-configs/mkhomedir" <<EOF
Name: activate mkhomedir
Default: yes
Priority: 900
Session-Type: Additional
Session:
        required                        pam_mkhomedir.so umask=0022 skel=/etc/skel
EOF

```
then activated with
```

sudo pam-auth-update
sudo systemctl restart sssd

```
That should get it to where it needs to be... Just like Fedora.

---

### Post by seb05mar86 on 2022-12-03
I know that there are differences with the create from home directory. Fedora also uses oddjob, but I don't get that far.


kinit administrator works
```
krbtgt/AD.DOMAIN.COM@AD.DOMAIN.COM
Etype (skey, tkt): aes256-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96

```
adcli or net (samba) cannot authenticate via Kerberos in my opinion. -> no /etc/krb5.keytab is created -> sssd cannot authenticate.

---

### Post by seb05mar86 on 2022-12-03
Very few people write in their tutorial which Windows Server version they are using and if they do, it is certainly not an Insider/Preview version.

---

### Post by MAFoElffen on 2022-12-03
Just finishing my testing on Lunar daily Server & Desktop builds. Will spin up a Win Server Preview build  25246 and create a Domain to join to... 

You have me curious now.

---

### Post by seb05mar86 on 2022-12-03
Thanks, that you try it.

---

### Post by MAFoElffen on 2022-12-04
Status. My latest Lunar server is configured and waiting on the DC. The Windows Server 2022 Preview DC is waiting on Windows updates... 

At the moment it is at 23%. LOL. I've forgotten how torturous Windows updates can be sometimes. Getting there.

---

### Post by MAFoElffen on 2022-12-05
At first on boot I would notice a problem with sssd pending in the startup messages. Pointed to me having to tweak my /etc/sssd/sssd.conf file.

Okay... Joined the server to the Domain.... See attached.

Will ask you questions about yours tomorrow...

---

### Post by mIk3_08 on 2022-12-05
> **MAFoElffen said:**
> I've forgotten how torturous Windows updates can be sometimes. Getting there. Not only sometime but most of the time. I have heard lately here in our area (Philippines) that win 11 update removes some drivers of the new release laptops in the market. Technicians are struggling to use Win11 as they encounter problems in their devices that uses win 11 installed OS'es. And how come is that, Buyer of the gadget returned their units due to some failures or some components are not working properly. Does it mean that, MS Windows running to servers now. :P  Regards and cheers

---

### Post by MAFoElffen on 2022-12-05
please post the results of
```

sudo cat /etc/sssd/sssd.conf
ls -lh /etc/sssd/sssd.conf
sudo sssd -d9 -i
sudo systemctl status sssd

```

---

### Post by MAFoElffen on 2022-12-06
The long and short of it... I made sure that sssd loaded and ran without errors, that I could resolv (forward and reverse lookups) to the DC, that I could get a kerberos ticket (krb5.conf), and that "security = ADS" was uncommented in my smb.conf.

---

