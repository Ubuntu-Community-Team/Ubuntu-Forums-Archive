---
title: "mount --bind without root"
date: 2009-02-02
forum: Server Platforms
---

### Post by cmol on 2009-02-02
Hello

I'm making an administrative module in PHP to my server, that can add virtual ftp users.
When the user is added, I make the users homedir and a mount point in the homedir for a shared dir.

It could be adding the user 'michael'.

First I run a mysql query to add the user for login and specify homedir(logindir).

```
homedir: /media/storage/ftp/michael
```

Then I make the homedir, and make a mount dir

```
mountdir: /media/storage/ftp/michael/shared
```

The last thing I need to do, is mount the shared dir into the 'shared' folder in the homedir

```
My shared dir i located in: /media/storage/shared
```

If I execute the code,

```
sudo mount --bind /media/storage/shared /media/storage/ftp/michael/shared
```

everything works fine, but the idea is to make it work from the php.

The problem is that I can't run the code without root access.
Is there any way to work around this without giving the php root access?

---

### Post by cmol on 2009-02-02
I was planning on using symlinks, but they don't work under ftp.

---

### Post by cmol on 2009-02-03
If somebody have a different way of solving this, I would be glad to hear that to.

---

### Post by cmol on 2009-02-03
Hello

I'm making an administrative module in PHP to my server, that can add virtual ftp users.
When the user is added, I make the users homedir and a mount point in the homedir for a shared dir.

It could be adding the user 'michael'.

First I run a mysql query to add the user for login and specify homedir(logindir).

```
homedir: /media/storage/ftp/michael
```

Then I make the homedir, and make a mount dir

```
mountdir: /media/storage/ftp/michael/shared
```

The last thing I need to do, is mount the shared dir into the 'shared' folder in the homedir

```
My shared dir i located in: /media/storage/shared
```

If I execute the code,

```
sudo mount --bind /media/storage/shared /media/storage/ftp/michael/shared
```

everything works fine, but the idea is to make it work from the php.

The problem is that I can't run the code without root access.
Is there any way to work around this without giving the php root access?

---

### Post by overdrank on 2009-02-03
Please do not make multiple threads on the same issue. Threads merged :)

---

### Post by cmol on 2009-02-03
> **overdrank said:**
> Please do not make multiple threads on the same issue. Threads merged :)

Sorry :) Got the feeling that I had posted it the wrong place, so thanks for moving it to the server part :)

---

