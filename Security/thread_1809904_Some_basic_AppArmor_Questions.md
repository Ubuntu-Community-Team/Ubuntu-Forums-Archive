---
title: "Some basic AppArmor Questions:"
date: 2011-07-22
forum: Security
---

### Post by stevennlv on 2011-07-22
OK,

I've been digging through AppArmor and I'm suffering from information overload. I have about a dozen book marks on the subject. Most of them are muiltipage wiki's. My eyes are swimming and I'm sure I'm probably missing something obvious. But I have some basic questions:

I downloaded and installed the default profiles last night with the commands:

sudo apt-get install apparmor-profiles
sudo aa-enforce /etc/apparmor.d/*

Now, if I understand correctly that put the profiles in to "enforce" mode? (Which is what I want.)

I'm not 100% clear on which profiles are included in the default package?

I only have two net applications that I use. They are Fire Fox and Google Earth. I know a profile for Fire Fox is included in the defaults. But, is there one for Google Earth?

If not where is a trustworthy place to get a good general use profile for GE? Is there one?

Once I find it how do I install a lone profile and not mess up everything else with AppArmor in the process?

Is AppArmor and its profiles included in the default repositories? Is it updated by the system update manager? If not then how would I go about setting it up so that it is updated by the system update manager in the Ubuntu Software Center?

Any help would be greatly appreciated.

Thanks.

---

### Post by bodhi.zazen on 2011-07-22
> **stevennlv said:**
> OK,

I've been digging through AppArmor and I'm suffering from information overload. I have about a dozen book marks on the subject. Most of them are muiltipage wiki's. My eyes are swimming and I'm sure I'm probably missing something obvious. But I have some basic questions:

Yes this is the problem with apparmor. It is easier to learn, but there is still a learning curve and the documentation is not maintained. 

Keep in mind it is a community wiki, so, if you do not like the documentation feel free to contribute, as a community member it is your responsibility to contribute. Otherwise do not complain about the documentation.

> I downloaded and installed the default profiles last night with the commands:

sudo apt-get install apparmor-profiles
sudo aa-enforce /etc/apparmor.d/*

Now, if I understand correctly that put the profiles in to "enforce" mode? (Which is what I want.)

That is correct. The apparmor sticky at the top of this page 

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Has information condensed in a few posts, I suggest you read it again.

See also:

```
sudo aa-status
```

> I'm not 100% clear on which profiles are included in the default package?

```
ls /etc/apparmor.d/
```

See also: [http://www.ubuntugeek.com/what-package-is-that-file-in.html](http://www.ubuntugeek.com/what-package-is-that-file-in.html)

> I only have two net applications that I use. They are Fire Fox and Google Earth. I know a profile for Fire Fox is included in the defaults. But, is there one for Google Earth?

If not where is a trustworthy place to get a good general use profile for GE? Is there one?

Not that I know of, you have to write one yourself.

Again, a downside of apparmor.

> Once I find it how do I install a lone profile and not mess up everything else with AppArmor in the process?

Is AppArmor and its profiles included in the default repositories? Is it updated by the system update manager? If not then how would I go about setting it up so that it is updated by the system update manager in the Ubuntu Software Center?

Any help would be greatly appreciated.

Thanks.

You install profiles in /etc/apparmor.d 

Yes a malfunctioning profile can disable apparmor.

You have to keep reading.

The reasons you cited in this thread are why I switched to Fedora

selinux in Fedora 15 is hands down more mature, in general works out of the box, and there are better tools, both graphical an otherwise, to manage selinux.

In Fedora you could run GE in the (selinux) sandbox

Example: [http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html](http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html)

Pick you poison =)

---

