---
title: "upload folder/file into my server command line"
date: 2009-06-13
forum: Server Platforms
---

### Post by Heeter on 2009-06-13
Hi all,

I would like to know how to upload a file or a folder into my Ubuntu 8.10 Server 64bit from my Ubuntu 8.10 desktop?

I am using terminal->ssh for accessing my server from my desktop.

Thanks

Heeter

---

### Post by albinootje on 2009-06-13
> **Heeter said:**
>  I would like to know how to upload a file or a folder into my Ubuntu 8.10 Server 64bit from my Ubuntu 8.10 desktop?

```

scp -r your_directory_to_upload/ your_remote_username@your_server_ip:

```
For just 1 file :
```

scp your_file_to_upload your_remote_username@your_server_ip:

```
That will put the file/directory in your user's home directory.
See also : man scp (and : man sftp)

---

### Post by Heeter on 2009-06-13
Thanks a whole, bunch

I am doing this now. I am wondering, how do I monitor it's upload progress? I don't a progress bar.

Am I supposed to see one?

This is for a 510 meg file. Don't know if it's done.

Thanks


Heeter

---

### Post by albinootje on 2009-06-13
> **Heeter said:**
>  I am wondering, how do I monitor it's upload progress? I don't a progress bar.

You should see something with scp. Here's example output :
```

wine_1.0-0.23.uk_i386.deb         100%   37MB  12.2MB/s   00:03    

```
During the copying you should see percentage and transfer speed, and estimated time left.

---

### Post by cariboo on 2009-06-14
You could also use sftp from your desktop to your server. Open nuatilus and in the location bar type:

```
sftp://user@server
```

Your home directory on the server will show up in nautilus, open another tab and use copy and paste the file you want to copy.

---

