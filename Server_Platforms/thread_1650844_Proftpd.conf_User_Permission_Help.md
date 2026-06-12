---
title: "Proftpd.conf User Permission Help"
date: 2010-12-22
forum: Server Platforms
---

### Post by ptmuldoon on 2010-12-22
I'm trying to modify my proftpd config file to use a usergroup that lets users read and download from a set of folders, and upload only into one designated upload folder.

I think i'm close to having it correct, but am still new to setting up the config file, and how the use of LIMIT and AllowGroup and DenyGroup works.

Essentially, I have a Media directory, with multiple subdirectories.  The user should be able to read and download only from any of the subdirectories, except for the Uploads folder.  And the Upload folder should permit the creation of folders and uploading only.

I have this currently in my config file, but its not working as it should.
> 
<Directory /mnt/public/raid/Media/>
	Umask 002
	AllowOverwrite on

	<Limit STOR STOU>
      DenyGroup ftpusers
    </Limit>
</Directory>

<Directory /mnt/public/raid/Media/Uploads/>
	Umask 002
	AllowOverwrite on
	
	<Limit READ CWD>
		AllowGroup ftpusers
	</Limit>
</Directory>


---

