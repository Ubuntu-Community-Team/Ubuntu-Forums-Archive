---
title: "Porting over a windows file server to linux"
date: 2008-06-23
forum: Security
---

### Post by froyd on 2008-06-23
Hi,

I have a project going on in my company to move 3 file servers and consolidate into one big one. We are most likely doing everything in the bill boxes (win) but i have the option to prove that a linux solution can work too.
And to do this i would like to count with some support from this forum. I do have some level of experience in the linux world but notting like moving windows services to a linux box. Since everything im going to be dealing with is production, i really need this to work 200% in order to convince my manager. So lets go.

I Cant set up the samba file share without any problems, i can also join the computer to our domain, but, im not sure how the permissions are going to be affected. The primary thing in here now is to keep all the permissions the same way they are. In a windows word i can restore the files from a backup tape because this way the permissions are going to be kept. Can i restore the backup tapes to a ext2 file system and still preserve the permissions ? What if i restore the files to a windows enviroment, how can i move them to the samba box preserving the permissions ( i dont recall that beeing possible ).

As soon as this great community help me out on this, we can discuss then ill post other concerns i have.

Thank you all.
Fred

---

### Post by hyper_ch on 2008-06-24
what permissions are you talking about? I don't get that point here... besides you should use ext3 and not ext2 ;)

Do you mean windows file permissions? Or linux U[ser]G[roup]W[orld] permissions?

And you meant to write "you can setup samba" or "you can't setup samba"?

---

### Post by froyd on 2008-06-24
> **hyper_ch said:**
> what permissions are you talking about? I don't get that point here... besides you should use ext3 and not ext2 ;)

Do you mean windows file permissions? Or linux U[ser]G[roup]W[orld] permissions?

And you meant to write "you can setup samba" or "you can't setup samba"?

Sorry ,

I meant i CAN setup samba properly. 
The other thing is , we need all our WINDOWS (AD) share and file permissions to be fully functional. And i will be using ext3.

Thank you

---

### Post by hyper_ch on 2008-06-24
no clue about AD... try the ubuntu wiki: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

---

### Post by HermanAB on 2008-06-24
You should not have a problem.  If you do, go to the Samba web site and read the Official Howto.

Start by duplicating some of the non-critical data, then test it for a few weeks, before moving the rest over.

---

