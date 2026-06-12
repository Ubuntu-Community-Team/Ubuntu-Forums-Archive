---
title: "SMBFS Mount and File Reading / Xfer"
date: 2010-05-26
forum: Server Platforms
---

### Post by Gohtar on 2010-05-26
I have a Ubuntu 9.10 server which mounts a share from a Windows Server 2003.

My mount line is below, I have this in the fstab

//cpf-pflm/pflm/pflm /mnt/pflmReports smbfs credentials=/root/kokoScripts/.smbcreds,uid=1000,gid=1000

I have a script that reads a ~7 meg, Tab deliminated, text file from that mount point and inserts the data in to a mysql database using the LOCAL INFILE method.

The file is formatted correctly and you can open it in Excel and read just fine in Windows.  

In the MySQL database a lot of the data becomes unformatted and inserts in to the wrong columns.

For example:
Cols in the file (name,address,city,state,email) (commas = \t)
Test Data: test name,123 fake st, fake, CA, [email]fake@fake.com[/email]

When I open the file in VIM you see
test name, 123 fake [email]stfake@fake.com[/email]
It somehow disregarded the city and state and massed the email in to the address

I tried to copy the file to /tmp and I got the same result when opening it in vim

When I copied the file to the server using WinSCP and opened it in vim everything was perfect.

This happens constantly and consistently to the same lines in the text file.  The text file has 6300+ lines in it.

Since this only happens when reading from the smb share or copying from the smb share then reading, I figure it has something to do with that share.

Does anyone have any idea why something like this would happen?

Thanks

---

### Post by capscrew on 2010-05-26
> **Gohtar said:**
> I have a Ubuntu 9.10 server which mounts a share from a Windows Server 2003.

My mount line is below, I have this in the fstab

//cpf-pflm/pflm/pflm /mnt/pflmReports smbfs credentials=/root/kokoScripts/.smbcreds,uid=1000,gid=1000

I have a script that reads a ~7 meg, Tab deliminated, text file from that mount point and inserts the data in to a mysql database using the LOCAL INFILE method.

The file is formatted correctly and you can open it in Excel and read just fine in Windows.  

In the MySQL database a lot of the data becomes unformatted and inserts in to the wrong columns.

For example:
Cols in the file (name,address,city,state,email) (commas = \t)
Test Data: test name,123 fake st, fake, CA, [email]fake@fake.com[/email]

When I open the file in VIM you see
test name, 123 fake [email]stfake@fake.com[/email]
It somehow disregarded the city and state and massed the email in to the address

I tried to copy the file to /tmp and I got the same result when opening it in vim

When I copied the file to the server using WinSCP and opened it in vim everything was perfect.

This happens constantly and consistently to the same lines in the text file.  The text file has 6300+ lines in it.

Since this only happens when reading from the smb share or copying from the smb share then reading, I figure it has something to do with that share.

Does anyone have any idea why something like this would happen?

Thanks

This is just a guess, but worth passing along.  In the fstab line you are using smbfs.  This has been deprecated for some time now and should only be used older (NT?) filesystems.  I would try cifs instead.  The line would be ```
//cpf-pflm/pflm/pflm /mnt/pflmReports **[COLOR="Red"]cifs [/COLOR]**credentials=/root/kokoScripts/.smbcreds,uid=1000,gid=1000
```

I would remount the drive.  You can do > mount -a and remount all.

---

### Post by Gohtar on 2010-05-27
That fixed my problem, you are a miracle worker :)

Thanks

---

