---
title: "Thunderbird - different mailbox format on 64-bit?"
date: 2009-04-15
forum: The Cafe
---

### Post by infinitejones on 2009-04-15
I've always run 32-bit Ubuntu on my dual core laptop but in the run-up to the release of Jaunty I thought I'd give 64-bit a go. 

I've got /home in a separate partition so Thunderbird has always stored its mail there - that way, even if I reformat the root partition, I just re-install Thunderbird and it automatically finds my existing inboxes (I use Thunderbird to check several POP accounts) plus my mail folders and all my mail. I start it up after the re-install and bang, there it all is.

However, now that I've installed 64-bit Jaunty, Thunderbird is doing strange things. It's acting like I have no existing mailboxes anywhere and refuses to recognise the existing mail folders. 

I've even manually copied the old mailbox files (inbox & inbox.msf etc) into the new folders that Thunderbird creates after I manually re-entered all the account details - POP/SMTP servers for the different accounts, etc. But when I restart Thunderbird, it's as though there's nothing there at all. Nautilus confirms that the inbox files are the same size (2.8mb for one of them) but Thunderbird acts like they're completely empty. Same with my junk file filtering log and address book.

The **only** thing I can think of is that there's some difference in the files - an inbox file created by Thunderbird on a 32-bit OS is different from one created by Thunderbird on a 64-bit OS. Literally nothing else has changed.

Is that possible? Has anyone else encountered this? Any ideas how to fix this? Luckily I've got all the mail folders backed up in about four different places, so I can afford to experiment without losing my mail, but it's driving me mad...

---

### Post by manicman on 2009-04-15
Im sorry to say that I don't know what the problem is.
But from my own experiance 64 bit and 32 bit systems treat the mailbox files the same. My inbox is stored on my server and both my netbook (32 bit) and Desktop (64 bit) use it on a daily basis and I havent had any problems.

---

### Post by mips on 2009-04-15
This happens occasionally. Happened to friends last weekend and I had to fix it. 64bit mailbox format is identical to 32bit format.

Start thunderbird with the profile manager and see if you can load it that way otherwise I suggest you create a new profile and copy your mail across.

[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird)
[http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared]("http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared#Corrupt_or_empty_prefs.js")
[http://kb.mozillazine.org/Moving_address_books_between_profiles](http://kb.mozillazine.org/Moving_address_books_between_profiles)

---

### Post by ssam on 2009-04-15
i have shifted the entire thunderbird folder from 32bit powerpc macosx to 32bit powerpc linux to 64bit x86 linux with no problems. i think the format is completely cpu/platform independent.

i think you would do better to shift the whole folder, rather than mess around in the folders yourself.

---

### Post by mips on 2009-04-15
> **ssam said:**
> i have shifted the entire thunderbird folder from 32bit powerpc macosx to 32bit powerpc linux to 64bit x86 linux with no problems. **i think the format is completely cpu/platform independent.**

i think you would do better to shift the whole folder, rather than mess around in the folders yourself.

You are correct, it is cpu/platform independant.

Yes, the only that needs moving is the entire profile folder for the specific user.

---

