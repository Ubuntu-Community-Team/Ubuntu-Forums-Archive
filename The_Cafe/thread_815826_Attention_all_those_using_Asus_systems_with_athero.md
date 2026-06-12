---
title: "Attention all those using Asus systems with atheros network adapters"
date: 2008-06-02
forum: The Cafe
---

### Post by misshannah on 2008-06-02
From reading these forums I am not the only person struggling to get wireless working on my Asus laptop due to their lack of support with ubuntu. I recently emailed Asus requesting more support and I urge you all to do the same to ensure they recognise the problem. 

Here is a copy of what I sent via their online support form ([http://vip.asus.com/eservice/techserv.aspx):](http://vip.asus.com/eservice/techserv.aspx):)

Dear Asus.

It would be much appreciated if you provided more support those of us using linux - namely ubuntu. Ubuntu has a vast number of users, and from the forums ([www.ubuntuforums.org](www.ubuntuforums.org)) there are many users expericencing problems with your systems, particularly your atheros wireless network adapters. I purchased an Asus branded laptop becuase the Asus brand was strongly recommended to me. Most other features of this laptop have worked flawlessly with the Linux environment (plug 'n' play support).

However, with wireless being one of the most crucial aspects to notebook computer use, the lack of support has caused me a lot of grief as I am a full-time student who purchased this laptop soley for my studies.

I can guarantee that a vast number of users would be extremely grateful if some form of support was issued for your wireless network adapters.

Thanks in advance,
Hannah Pinkerton.

---

### Post by p_quarles on 2008-06-02
Moved to Community Cafe, since this is not a technical support request, but a development request.

---

### Post by ardvark71 on 2008-06-02
Hi...

Very nice letter. :)

And I certainly agree that manufacturer support (with drivers) is badly needed. 

Best Regards...

---

### Post by jrusso2 on 2008-06-02
> **misshannah said:**
> From reading these forums I am not the only person struggling to get wireless working on my Asus laptop due to their lack of support with ubuntu. I recently emailed Asus requesting more support and I urge you all to do the same to ensure they recognise the problem. 

Here is a copy of what I sent via their online support form ([http://vip.asus.com/eservice/techserv.aspx):](http://vip.asus.com/eservice/techserv.aspx):)

Dear Asus.

It would be much appreciated if you provided more support those of us using linux - namely ubuntu. Ubuntu has a vast number of users, and from the forums ([www.ubuntuforums.org](www.ubuntuforums.org)) there are many users expericencing problems with your systems, particularly your atheros wireless network adapters. I purchased an Asus branded laptop becuase the Asus brand was strongly recommended to me. Most other features of this laptop have worked flawlessly with the Linux environment (plug 'n' play support).

However, with wireless being one of the most crucial aspects to notebook computer use, the lack of support has caused me a lot of grief as I am a full-time student who purchased this laptop soley for my studies.

I can guarantee that a vast number of users would be extremely grateful if some form of support was issued for your wireless network adapters.

Thanks in advance,
Hannah Pinkerton.

Strange that in previous versions Atheros worked great.  What changed?  I think they changed the way wireless works and maybe are trying to fix some drivers and breaking others in the processes.

---

### Post by PartisanEntity on 2008-06-02
> **misshannah said:**
> From reading these forums I am not the only person struggling to get wireless working on my Asus laptop due to their lack of support with ubuntu. I recently emailed Asus requesting more support and I urge you all to do the same to ensure they recognise the problem. 

Here is a copy of what I sent via their online support form ([http://vip.asus.com/eservice/techserv.aspx):](http://vip.asus.com/eservice/techserv.aspx):)

Dear Asus.

It would be much appreciated if you provided more support those of us using linux - namely ubuntu. Ubuntu has a vast number of users, and from the forums ([www.ubuntuforums.org](www.ubuntuforums.org)) there are many users expericencing problems with your systems, particularly your atheros wireless network adapters. I purchased an Asus branded laptop becuase the Asus brand was strongly recommended to me. Most other features of this laptop have worked flawlessly with the Linux environment (plug 'n' play support).

However, with wireless being one of the most crucial aspects to notebook computer use, the lack of support has caused me a lot of grief as I am a full-time student who purchased this laptop soley for my studies.

I can guarantee that a vast number of users would be extremely grateful if some form of support was issued for your wireless network adapters.

Thanks in advance,
Hannah Pinkerton.

I think you sent the email to the wrong company, Asus is not responsible for the development of drivers for a card made by Atheros. You should have sent the email to Atheros?

I have always been quite happy with the Ubuntu compatibility of my Asus A6K.

---

### Post by lisati on 2008-06-02
> **PartisanEntity said:**
> I think you sent the email to the wrong company, Asus is not responsible for the development of drivers for a card made by Atheros. You should have sent the email to Atheros?

I have always been quite happy with the Ubuntu compatibility of my Asus A6K.

+1: My Toshiba laptop has networking components made by Atheros.

---

### Post by Tomatz on 2008-06-02
> **misshannah said:**
> From reading these forums I am not the only person struggling to get wireless working on my Asus laptop due to their lack of support with ubuntu. I recently emailed Asus requesting more support and I urge you all to do the same to ensure they recognise the problem. 

Here is a copy of what I sent via their online support form ([http://vip.asus.com/eservice/techserv.aspx):](http://vip.asus.com/eservice/techserv.aspx):)

Dear Asus.

It would be much appreciated if you provided more support those of us using linux - namely ubuntu. Ubuntu has a vast number of users, and from the forums ([www.ubuntuforums.org](www.ubuntuforums.org)) there are many users expericencing problems with your systems, particularly your atheros wireless network adapters. I purchased an Asus branded laptop becuase the Asus brand was strongly recommended to me. Most other features of this laptop have worked flawlessly with the Linux environment (plug 'n' play support).

However, with wireless being one of the most crucial aspects to notebook computer use, the lack of support has caused me a lot of grief as I am a full-time student who purchased this laptop soley for my studies.

I can guarantee that a vast number of users would be extremely grateful if some form of support was issued for your wireless network adapters.

Thanks in advance,
Hannah Pinkerton.

I have an asus eeepc with an atheros card, it works flawlessly under ubuntu.

This should get your atheros card working (it worked for me):

```
sudo apt-get install build-essential

wget 'http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz'

tar zxvf madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make clean

make

sudo make install

sudo shutdown -r now

```

;)

---

### Post by HunterThomson on 2008-06-02
Yes everybody send emails to atheros telling them to work with open source community to develop free open source drivers.

However, I think a lot of people are having problems with there ASUS wireless because they don't read the forums.

As far as I know all ASUS laptops use atheros wireless chipsets. You can use the MadWiFi driver.

[http://madwifi.org/](http://madwifi.org/)

---

### Post by misshannah on 2008-06-02
I've already tried everything I've seen on the forums and I'm still having issues. The wireless works but very poor signal. Thanks for the tips though.

---

### Post by quanumphaze on 2008-06-02
Kajaste has made a nice script to automatically install Madwifi from SVN

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

It worked for my 5005g

---

