---
title: "Zip Bombs: 42KB becomes 4600 Terrabytes"
date: 2012-10-04
forum: Security
---

### Post by yeehi on 2012-10-04
I was amazed that data could be compressed so much.
Have you ever encountered these [zip bombs]("http://en.wikipedia.org/wiki/Zip_bomb") before?

I wonder how long it would take to fully unpack such an archive, if you actually had the storage available. Would you notice the CPU activity or hear the data being written to the drive, do you think?

---

### Post by Stonecold1995 on 2012-10-05
I've never encountered one "in the wild", although I have downloaded them just for fun.  If you extract a zip-bomb, it won't do anything to your computer though, it'll just create 16 smaller zip-bombs.  If you decompress one of those it'll yield 16 more zip-bombs.  As such, they're not going to "explode" when someone opens them, they're just used by malware authors to knock out anti-virus software so malware can work without needing to watch its back.  What happens is, a malicious program may plant a zip bomb somewhere near it as bait for AV software.  The program will wait until the anti-virus comes up for a routine scan, and it'll wait, "hiding" behind the zip-bomb.  When the anti-virus reaches the bomb, it'll try to open it, all in its limited memory.  1 file becomes 16, which becomes 256, and it goes on until the memory is full.  In reality though, the computer never runs out of memory because each process is only allowed to use so much memory, after it hits its limit it crashes itself to protect the rest of the computer from an OOM (Out-Of-Memory) event.  When this happens to an anti-virus program as it's trying to dig into the file for malware, the software simply crashes and exits, while leaving the rest of the computer unharmed.  The malware will detect this, and will then use that opportunity to do whatever it wants, without having to worry about AV software that might be right around the corner.  However, most anti-virus software today recognizes a zip-bomb when it sees one, and will skip over it, alerting the user that the computer might be infected with malware.

As for your questions, no, you wouldn't notice disk space being used because zip-bombs only decompress in an anti-virus program's memory, not to the disk.  Most manual archive-opening programs don't even *have* a recursive opening mode for this very reason.  I don't think you'd notice much extra work by the CPU, because zip-bombs work so fast they can knock out an inadequately protected anti-virus program in seconds, while only using a fraction of the total computer's memory.

The zip bomb you're talking about is one of the first ones created, called 42.zip.  There are other ones, and there was one I saw that was 6 kilobytes, yet expanded to 4 zettabytes, seriously.  And I saw another, an XML-based decompression bomb called "[billion laughs]("https://en.wikipedia.org/wiki/Billion_laughs")", which basically crashes a web browser by causing the XML parser to run out of memory (most today though will detect such recursive expansion and simply not try to parse the booby-trapped XML).

If you are curious about how it works, you can download 42.zip from [here]("http://www.unforgettable.dk/").  And the really, really powerful one from [here]("https://thepiratebay.se/torrent/4739982/ZIP-bomb_-_Insanely_huge_ZIP-archive_(4ZB)") (downloading these are safe, and you can even open it.  But if you try to recursively extract it it'll take up a LOT of memory, and old AV software will crash upon scanning it).

Sorry for the long post, it's just that I find all kinds of logic bombs really interesting. ^^

---

### Post by yeehi on 2012-10-05
Thank you so much for your very interesting reply.
 
4 zettabytes... that is absolutely enormous! That is over 4000 million terabytes! (I think I can get a handle on terabytes, but anything larger is difficult to conceive. A petabyte is 1024 terabytes, which I can imagine.)

I suppose compression must be a very simple, efficient process when every bit in the file is a 0. That must be how such a gargantuan quantity of data could be reduced to such a small file size.

I noticed that the 42zip file is password protected. I didn't know you could do that with zip files - I thought you needed 7zip to do that with them. Would that locking used be equivalent to encrypting the archive?

---

### Post by Stonecold1995 on 2012-10-05
Locking?  It *is* encryption (although very weak, considering the password is "42").  Encrypted ZIP files use an encryption method called ZipCrypto (a proprietary format), whereas 7z files use AES.  And it's only password-protected so that you don't download it, and have it immediately crash your AV software if it's set to scan all downloads.  It allows you to download the file safely, and open it only when you want to.

---

### Post by yeehi on 2012-10-06
> **Stonecold1995 said:**
> Locking?  It *is* encryption...

Thank you for that interesting concept, Stonecold1995!

---

### Post by Scott Harrison on 2012-10-06
> **Stonecold1995 said:**
> I've never encountered one "in the wild", although I have downloaded them just for fun.  If you extract a zip-bomb, it won't do anything to your computer though, it'll just create 16 smaller zip-bombs.  If you decompress one of those it'll yield 16 more zip-bombs.  As such, they're not going to "explode" when someone opens them, they're just used by malware authors to knock out anti-virus software so malware can work without needing to watch its back.  What happens is, a malicious program may plant a zip bomb somewhere near it as bait for AV software.  The program will wait until the anti-virus comes up for a routine scan, and it'll wait, "hiding" behind the zip-bomb.  When the anti-virus reaches the bomb, it'll try to open it, all in its limited memory.  1 file becomes 16, which becomes 256, and it goes on until the memory is full.  In reality though, the computer never runs out of memory because each process is only allowed to use so much memory, after it hits its limit it crashes itself to protect the rest of the computer from an OOM (Out-Of-Memory) event.  When this happens to an anti-virus program as it's trying to dig into the file for malware, the software simply crashes and exits, while leaving the rest of the computer unharmed.  The malware will detect this, and will then use that opportunity to do whatever it wants, without having to worry about AV software that might be right around the corner.  However, most anti-virus software today recognizes a zip-bomb when it sees one, and will skip over it, alerting the user that the computer might be infected with malware.

As for your questions, no, you wouldn't notice disk space being used because zip-bombs only decompress in an anti-virus program's memory, not to the disk.  Most manual archive-opening programs don't even *have* a recursive opening mode for this very reason.  I don't think you'd notice much extra work by the CPU, because zip-bombs work so fast they can knock out an inadequately protected anti-virus program in seconds, while only using a fraction of the total computer's memory.

The zip bomb you're talking about is one of the first ones created, called 42.zip.  There are other ones, and there was one I saw that was 6 kilobytes, yet expanded to 4 zettabytes, seriously.  And I saw another, an XML-based decompression bomb called "[billion laughs]("https://en.wikipedia.org/wiki/Billion_laughs")", which basically crashes a web browser by causing the XML parser to run out of memory (most today though will detect such recursive expansion and simply not try to parse the booby-trapped XML).

If you are curious about how it works, you can download 42.zip from [here]("http://www.unforgettable.dk/").  And the really, really powerful one from [here]("https://thepiratebay.se/torrent/4739982/ZIP-bomb_-_Insanely_huge_ZIP-archive_(4ZB)") (downloading these are safe, and you can even open it.  But if you try to recursively extract it it'll take up a LOT of memory, and old AV software will crash upon scanning it).

Sorry for the long post, it's just that I find all kinds of logic bombs really interesting. ^^
Thank you Stonecold, that was a most interesting brief on the topic! :popcorn:
Definitely an intriguing concept.

---

