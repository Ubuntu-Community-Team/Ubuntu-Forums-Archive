---
title: "Sharing server:/var/www with my desktop NFS vs. proftpd"
date: 2008-10-01
forum: Server Platforms
---

### Post by botfish on 2008-10-01
I have a server running Ubuntu Server 8.04, and a desktop running Ubuntu Desktop 8.04, and I want to share server:/var/www with the desktop. The server is for development purposes and is not intended to be made public.

My first idea as to use the NFS protocol.

I changed the owner:group of server:/var/www to myself:myself.
I can successfully mount server:/var/www with rw access and read/modify files.

However when I create a file in server:/var/www my default desktop umask 022 (-rw-------) is applied. Documents in my webroot need to be 755. So I have concluded that, unless I’m missing something, NFS will not meet my requirements.

My second idea is to use proftpd.

How do I configure proftp so that I can log in as myself and access server:/var/www ?

Thanks for any help.

---

### Post by lykwydchykyn on 2008-10-01
Have you considered sshfs?

proftpd has a decent webmin module, if you're into webmin.  

Or if you just want to deal with the config file, just tack this on the end of the default config:

```

<Global>                                                                                            
DefaultChdir /var/www                                                                               
DefaultRoot /var/www                                                                                
</Global>  

```

---

### Post by windependence on 2008-10-02
You can use sftp right in Nautilus or Konqueror. You can drag and drop files right into and off of the web server. In Windows you can also use WinSCP and do the same thing. No need to mess with NFS.

-Tim

---

