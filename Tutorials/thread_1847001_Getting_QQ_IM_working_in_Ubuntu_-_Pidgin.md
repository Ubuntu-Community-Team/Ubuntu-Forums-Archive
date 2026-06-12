---
title: "Getting QQ IM working in Ubuntu - Pidgin"
date: 2011-09-20
forum: Tutorials
---

### Post by nicknefarious on 2011-09-20
To use QQ in Ubuntu 11.04 Natty onwards you need to install Pidgin IM. It is a multiple protocol IM client. See here [http://pidgin.im/]("http://pidgin.im/"). It is easy to find in the Software Centre in Ubuntu 11.04 onwards. Currently in  Pidgin however the QQ protocol is either out of date or has problems with the QQ security verifications. By adding the PPA on this page and following the instruction to install libqq-pidgin - [http://code.google.com/p/libqq-pidgin/wiki/UbuntuUsers]("http://code.google.com/p/libqq-pidgin/wiki/UbuntuUsers") from the Google Code project you can quickly and easily install their new libqq-pidgin package and this will allow you to use QQ in Ubuntu without any problems. Install it and check it out.

To do all this all you need to do is add the PPA and install as follows in a terminal...

```
sudo add-apt-repository ppa:lainme/libqq
sudo apt-get install libqq-pidgin
```

---

### Post by IAmCorbin on 2012-04-06
I have installed pidgin 2.10.3

and then:

sudo add-apt-repository ppa:lainme/libqq
sudo apt-get install libqq-pidgin


and I can see QQ in pidgin but then whenn I try and enable an account I get:

&#23562;&#25964;&#30340;&#29992;&#25143;&#65292;&#24744;&#30340;QQ&#29256;&#26412;&#24050;&#32463;&#20572;&#27490;&#20351;&#29992;&#65292;
&#35831;&#21040;[http://hi.qq.com](http://hi.qq.com)
&#19979;&#36733;&#24182;&#23433;&#35013;&#26368;&#26032;&#30340;QQ&#29256;&#26412;&#12290;
&#32473;&#24744;&#24102;&#26469;&#19981;&#20415;&#65292;&#25964;&#35831;&#35845;&#35299;&#65281;

Which I believe is telling me to update to the latest version of QQ? Is this due to outdated libqq-pidgin code?

---

### Post by Hotwheelz79 on 2012-05-22
> **IAmCorbin said:**
> I have installed pidgin 2.10.3

and then:

sudo add-apt-repository ppa:lainme/libqq
sudo apt-get install libqq-pidgin


and I can see QQ in pidgin but then whenn I try and enable an account I get:

&#23562;&#25964;&#30340;&#29992;&#25143;&#65292;&#24744;&#30340;QQ&#29256;&#26412;&#24050;&#32463;&#20572;&#27490;&#20351;&#29992;&#65292;
&#35831;&#21040;[http://hi.qq.com](http://hi.qq.com)
&#19979;&#36733;&#24182;&#23433;&#35013;&#26368;&#26032;&#30340;QQ&#29256;&#26412;&#12290;
&#32473;&#24744;&#24102;&#26469;&#19981;&#20415;&#65292;&#25964;&#35831;&#35845;&#35299;&#65281;

Which I believe is telling me to update to the latest version of QQ? Is this due to outdated libqq-pidgin code?

Hi,

I got it working for a friend as  recently as Saturday following the steps listed 

But apparently it has since stopped working sighting temporary login restrictions have been applied.

I haven't checked in with my friend today to see if this is still the case.

Thanks.

:-)

---

### Post by dandyling on 2012-05-25
> **Hotwheelz79 said:**
> Hi,

I got it working for a friend as  recently as Saturday following the steps listed 

But apparently it has since stopped working sighting temporary login restrictions have been applied.

I haven't checked in with my friend today to see if this is still the case.

Thanks.

:-)

I have just recently installed Ubuntu 12.04 and one of the first thing I tried was to get it working with Empathy..  and failed.. 

Do tell me if your friend get it to work.  Thanks :)

---

### Post by Ordes on 2012-07-16
i never had long luck with QQ and linux. even when it was running with pidgin. it was never really stable to me. i therefore just use the web version 
[http://web2.qq.com/webqqpic/](http://web2.qq.com/webqqpic/)

---

### Post by lainme on 2012-08-20
The QQ 2010 protocol is deprecated, but the libqq-pidgin is not upgraded for the new protocol.

Here is another one for pidgin: [https://github.com/xiehuc/pidgin-lwqq](https://github.com/xiehuc/pidgin-lwqq)

Currently there is no deb package for pidgin-lwqq, but you can refer to this page for compiling it yourself: [https://github.com/xiehuc/pidgin-lwqq/wiki/install-on-ubuntu](https://github.com/xiehuc/pidgin-lwqq/wiki/install-on-ubuntu)

After install, open pidgin and choose 'WebQQ' as the protocol to add your account.

---

### Post by rd79 on 2013-05-28
this works for me
[TABLE]
[TR]
[TD="class: votecell"]     down vote       
              [/TD]
                [TD="class: answercell"]     for your Linux needs please consider using:
  [http://qqchat.qq.com](http://qqchat.qq.com) (QQ for Facebook.. it's wickedly good!) 

[/TD]
[/TR]
[/TABLE]

---

