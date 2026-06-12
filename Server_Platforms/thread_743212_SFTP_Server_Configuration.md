---
title: "SFTP Server Configuration"
date: 2008-04-02
forum: Server Platforms
---

### Post by NDLunchbox on 2008-04-02
Hi, I'm a fairly new Linux Sys Admin (only been using Linux for about a year and a half an my shop is almost 100% Microsoft so I've been kind of going it alone, but I digress) and I need some help / suggestions on setting up an SFTP server in our DMZ to transfer large files too and from clients.  Security will be very important.

I was planning on installing Ubuntu Server on an older 4 way 700MHz PIII I have lying around, locking it down with Bastille and only opening Port 22 on our firewall to it.  I will use OpenSSH as the SFTP server.  But I have some questions on the mechanics of how this will work.

Is the best way to go about this setting up a user account in Linux for each client?  Is there a way I can limit them to only seeing their home directory for uploads / downloads?  How about limiting them to file transfers with no shell access?

Then I'll need to setup a few accounts for internal users to go retrieve the data and from the clients and upload our products to their directories... is there a way I can do that without resorting to giving them Root access?

Finally, any more security options I can take since this will be in the DMZ with SSH running on it?

Any other suggestions on how to securely exchange files with clients?  I put my foot down and said no more FTP.

---

### Post by craigp84 on 2008-04-02
Hi NDLunchbox,

OpenSSH is absolutely a possible solution for the requirements you've listed, and it will work. However, as i read through your post, i couldn't help but think "this sounds like a job for FTP" :-)

Remember setting up encrypted FTP is very straightforward, and is widely supported by client applications. Certainly more widely supported in the Windows client world in terms of nice GUI clients than openssh has currently.

Moulding SSH to fit your list of requirements will take significantly more work, and has many more potential downfalls -- there's a lot of scope for you to make simple configuration mistakes and open up your box to shell access from your users (and anyone they tell the password to! :-)

The requirements you've listed read pretty much like the features list of vsftpd, or many of the other ftpds.

In terms of practicalities, your quad core box will be wasted on sftp -- it's single threaded :-) no matter how many clients you have connected -- they're all on the one processor. That being said, one of those processors will be plenty to handle a the average business internet line saturated with client data.

Also, given that it's large files, it'll be reasonable to assume there will be some connection drops in the middle of some transfers. With sftp you start from the top again, with certain ftp client / servers you can continue from where you left off.

You will also need to create seperate user accounts on the box for your clients to implement the permissioning you're after too (one client cant see another client's files). With ftp, you can create user accounts that exist only within the FTP service. That would potentially be a more secure approach.

In terms of further lockdowns -- a good one would be to ensure your firewall is only allowing the necessary connections into the host (and none back out again -- don't let the bot's talk to their masters in the case that they do get in!).

So definately, put your foot down and say no to unencrypted ftp. Use a Securer FTP implementation; an encrypted one. SSL encrypted FTP is a good solution.

Hope it helps :-)

-c

---

### Post by NDLunchbox on 2008-04-02
Thanks!  I'm looking at VSFTPD now.

---

