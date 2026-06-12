---
title: "2gb data transfer limitation?"
date: 2007-09-30
forum: Server Platforms
---

### Post by bone2006 on 2007-09-30
I've installed ubuntu server and as far as I can remember I wasn't given a choice, which type of partition to select, so as far as I know it's ext3.  I have openssh server installed and a friend of mine who lives in another city needed to upload a large file and was not able to upload it.

After many tests there seems to be a 2gb limitation on the size of the file that he was able to upload.  He could upload any file up to 1gb.  Anyway of  over coming this limitation or could it be the client he was using?
He was using filezilla if I'm not mistaken

---

### Post by MJN on 2007-09-30
If you check the output of** mount **you can see what filesystem type each of your partitions/mounts are using. If it is ext3 then the filesize limitation is 16GB-2TB depending on cluster size (see [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) for further details of this and other FS types).

Assuming the filesystem is not your problem then this leaves the client and/or server - start by using a different client and see if you have any joy.

Sorry I can't be more helpful but I've never hit this problem before, and am not familiar with Filezilla, however a process of elimination will lead you towards pinpointing the cause.

Mathew

---

### Post by bone2006 on 2007-09-30
could it even be possible from a ubuntu server 7.04 cd to have the ability to select a file system that would not support 2GB files or larger?  I did everything with the ubuntu server CD.
Is there a command I can type to double check?  I'll try another client, I'll tell the person to try gftp to determine if it's a bug with the client.

going to get him to try GFTP

thanks

---

### Post by HermanAB on 2007-09-30
The common 2GB limit is actually a bug in many FTP clients.  If he is using Windoze, try the latest FileZilla.

Cheers,

Herman

---

### Post by bone2006 on 2007-10-01
Is filezilla aware of their bug?  I'd really do like filezilla and would like that they are at least aware of it.

he's using ubuntu as well

He tried GFTP, which acted different.  With filezilla, when he tried to upload anything over 2gb it would return that the file was already there asking him if he wants to resume or over write and either choice returned the same question over and over, so he couldn't get far in filezilla with uploads.

GFTP seemed to allow him to upload, but it wouldn't allow him to resume the upload like filezilla would.  For 2gb files and higher I'd really need something that resumes uploads/downloads

---

### Post by bone2006 on 2007-10-02
The upload worked fine with gftp, you just can't resume.  I reported the bug with filezilla, hopefully the bug will be fixed, since filezilla is my favorite client.

---

### Post by HermanAB on 2007-10-02
Lftp can resume and retry ad infinitum, but it is a command line tool.

This is such an old bug - I'm amazed that it is still in FileZilla.  They must have copied some code from another rather prehistoric project...

Cheers,

Herman

---

### Post by bone2006 on 2007-10-04
I reported the bug and I posted the version that I had from ubuntu's repository and my bug report was deleted indicating it wasn't a supported version, since it was outdated.  So I went to filezilla's website and downloaded the latest stable on, which is 3.0.1 and extracted it and ran it............samething.
If you try to upload something smaller than 2gb, no problem...... anything 2gb or older it will tell you the file is already there and asking if you want to resume or over write......eitherway it asks again.  If you click cancel and do a refresh no file is there.

I've tried other directories, made sure the the permissions are even 777 and I also checked using windows machine with a fresh copy of the latest filezilla.................same issue.  I've compared it to other programs and other ones work.

I replied to the comment when the bug report was closed that it's still an issue with the latest version.

I'm guessing maybe this issue wasn't tested or resolved in SFTP and maybe the majority of people do testing with just FTP.......just guessing though.

Hope it gets fixed, love filezilla and love that I can use it on both windows and linux

---

### Post by MJN on 2007-10-04
Don't be so hasty with the bug reports... Developer's hate nothing worse than trigger-happy 'bug' reporters!

I've just installed Filezilla (v3.0.1 on Vista) to give this a shot and was able to upload a 3GB file to my Dapper server (running openssh-server v4.2p1-7ubuntu3) without a problem.

Have you tried uploading a >2GB file from your machine _to itself_ using Filezilla? That way you can rule in/out any issue with your friend's machine and the connection between you.

Mathew

---

### Post by bone2006 on 2007-10-04
was it SFTP or FTP as i've mentioned a few times?

amazing......not working for me, not working for anybody I know trying to upload to my server, posted it and the developer found the bug. 

here's what the developer wrote:

**********
Found the problem, missing define in a makefile.

Will be fixed in next version.
**********

really glad to see this fixed as I really like filezilla

I'm guessing you didn't upload to an SFTP server, because I've tried it on my own server, a friends server both running ubuntu server and I've tried it on a client with vista and the latest windows and after 20 different tires it's the same conclusion.  Downloading is ok, but not upload.  So I'm guessing something is wrong on your end since the developer found the bug

---

### Post by MJN on 2007-10-05
No, definitely SFTP - I wouldn't dream of running an FTP server! ;)
 
I wonder if Filezilla keeps any logs? I'll have a look later.
 
Having said that, if you've had the bug confirmed then it's probably a moot point - you'll be back up and running in no time.
 
I'm sure it's likely that the bug only manifests itself under certain conditions, otherwise it'd be being wider reported (and indeed I would not be able to upload the 3GB file either).
 
What's the bug ID?
 
Cheers,
 
Mathew

---

### Post by MJN on 2007-10-05
I've just given this another go (with a 2.9GB zip file) and again it works fine - see the log below which may be of use:

```
Status:    Connecting to rugrat.newtonnet.co.uk:22...
Trace:    Going to execute "C:\Program Files\FileZilla Client\fzsftp.exe"
Response:    fzSftp started
Trace:    CSftpControlSocket::ConnectParseResponse(fzSftp started)
Command:    open "user@rugrat.newtonnet.co.uk" 22
Trace:    Looking up host "rugrat.newtonnet.co.uk"
Trace:    Connecting to 82.46.99.50 port 22
Trace:    Server version: SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.1
Trace:    Using SSH protocol version 2
Trace:    We claim version: SSH-2.0-PuTTY_Local:_Sep_19_2007_20:58:38
Trace:    Doing Diffie-Hellman group exchange
Trace:    Doing Diffie-Hellman key exchange with hash SHA-1
Trace:    Host key fingerprint is:
Trace:    ssh-rsa 2048 f2:54:71:c5:26:23:86:91:83:c1:28:21:5c:0c:dc:50
Trace:    Initialised AES-256 SDCTR client->server encryption
Trace:    Initialised HMAC-SHA1 client->server MAC algorithm
Trace:    Initialised AES-256 SDCTR server->client encryption
Trace:    Initialised HMAC-SHA1 server->client MAC algorithm
Command:    Pass: *********
Trace:    Sent password
Trace:    Access granted
Trace:    Opened channel for session
Trace:    Started a shell/command
Status:    Connected to rugrat.newtonnet.co.uk
Trace:    CSftpControlSocket::ConnectParseResponse()
Trace:    CSftpControlSocket::ResetOperation(0)
Trace:    CControlSocket::ResetOperation(0)
Trace:    CSftpControlSocket::FileTransfer(...)
Status:    Starting upload of C:\Temp\test.zip
Command:    cd "/home/user/Temp/"
Response:    New directory is: "/home/user/Temp"
Trace:    CSftpControlSocket::ResetOperation(0)
Trace:    CControlSocket::ResetOperation(0)
Trace:    CSftpControlSocket::SendNextCommand(0)
Trace:    FileTransferSend()
Command:    put "C:\Temp\test.zip" "test.zip"
Status:    local:C:\Temp\test.zip => remote:/home/user/Temp/test.zip
Trace:    Initiating key re-exchange (too much data sent)
Trace:    Doing Diffie-Hellman group exchange
Trace:    Doing Diffie-Hellman key exchange with hash SHA-1
Trace:    Initialised AES-256 SDCTR client->server encryption
Trace:    Initialised HMAC-SHA1 client->server MAC algorithm
Trace:    Initialised AES-256 SDCTR server->client encryption
Trace:    Initialised HMAC-SHA1 server->client MAC algorithm
Trace:    Initiating key re-exchange (too much data sent)
Trace:    Doing Diffie-Hellman group exchange
Trace:    Doing Diffie-Hellman key exchange with hash SHA-1
Trace:    Initialised AES-256 SDCTR client->server encryption
Trace:    Initialised HMAC-SHA1 client->server MAC algorithm
Trace:    Initialised AES-256 SDCTR server->client encryption
Trace:    Initialised HMAC-SHA1 server->client MAC algorithm
Trace:    FileTransferParseResponse()
Trace:    CSftpControlSocket::ResetOperation(0)
Trace:    CControlSocket::ResetOperation(0)
Status:    File transfer successful
Status:    Disconnected from server

```Note the two '*Initiating key re-exchange (too much data sent)*' trace sections - these occured at the 1GB data marks as per the SSH-2 protocol spec. This can often be changed by the client (it's not recommended to be any higher, or disabled entirely) but I can't see anywhere in Filezilla that allows this to be changed.

I'm wondering if perhaps you're having rekeying problems? Try running a transfer with the client logging running in verbose mode (it just adds the Trace lines) and this might give us some ideas - at the very least it should indicate any similarities/differences between our configurations.

Have you tried the latest nightly build? Presumably the developer has fixed the makefile in there?

Mathew

---

### Post by bone2006 on 2007-10-05
No I haven't tried the nightly build one yet, I didn't want to be a pain to the developer, just appreciate the software, so I thought I'd give it sometime.  I tried the latest stable from their website, but originally I tried the one that was in the repository here.

It may be a strange condition, since your saying you used SFTP as well.  I'm not sure what to think........ but the developer says that he's found the bug

id=21558

sorry for the ignorance, but how would I run verbose mode ?

---

### Post by MJN on 2007-10-05
Have you tried it with verbose logging?

---

### Post by steve.horsley on 2007-10-06
Sorry, I'm having trouble following this. Which product has the bug? Filezilla, openSSH? Whos bug ID is that - it's not an Ubuntu ID - I looked there.

---

### Post by MJN on 2007-10-06
> **bone2006 said:**
> sorry for the ignorance, but how would I run verbose mode ?

Sorry bone2006 - I somehow missed that question...

To log verbosely in Filezilla, go to Edit > Settings > Debug > Tick 'Debug Menu' and set level 3-Verbose.

The transaction log will then appear in the upper window for all connections and transfers.

As Steve mentioned, can you give us a link for the bug report?

Mathew

---

### Post by bone2006 on 2007-10-06
here's the link [http://tinyurl.com/2yvox7](http://tinyurl.com/2yvox7)

The bug is posted with filezilla themselves.  It's kind of a question I have, if I find a bug in the software that I currently get from ubuntu's repository I should submit the bug with the original develop and not with ubuntu........right?

MJN - I'll go a head and do the verbose settings as soon as I get home.  Appreciate the help and info

---

