---
title: "Question According FreeNX Server proxy (freenx-rdp freenx-media ...)"
date: 2009-03-05
forum: Server Platforms
---

### Post by seppl82 on 2009-03-05
Hey all,

i've successfully installed the freenx server on my Ubuntu Hardy.
Now i'm wondering what the freenx-rdp package is used for.
I've installed it and assumed that after the installation i am able to connect to my linux machine using the "Microsoft Remote Desktop Connection" tool.

But i can't connect to the machine with MS RDP.

Did i understood something wrong or do i just need to restart a service?

Kind Regards
/Seppl

---

### Post by jimmah6786 on 2009-05-15
> **seppl82 said:**
> Hey all,

i've successfully installed the freenx server on my Ubuntu Hardy.
Now i'm wondering what the freenx-rdp package is used for.
I've installed it and assumed that after the installation i am able to connect to my linux machine using the "Microsoft Remote Desktop Connection" tool.

But i can't connect to the machine with MS RDP.

Did i understood something wrong or do i just need to restart a service?

Kind Regards
/Seppl

Hey Seppl,

I was reading the description of this deb package and it seems like this is a package that handles RDP requests from clients to a windows machine. Sort of like a "hop" where the "hop" is your Linux box...

So if there are three machines:
1. Windows machine with RDP listening
2. Your linux box with freenx-server, and freenx-rdp running
3. The client who is trying to connect to machine #1

I believe that this package is so that machine #3 will use machine #2 to bounce its traffic to the Windows machine. NoMachine/Freenx has many expensive features, such as zlib'in the traffic stream and encryption of the stream.

I hope this was somewhat helpful, and please comment on any findings you might have stumbled upon that prove otherwise.

-Jim

---

