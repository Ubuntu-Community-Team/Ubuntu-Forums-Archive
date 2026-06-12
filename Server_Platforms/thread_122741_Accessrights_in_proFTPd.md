---
title: "Accessrights in proFTPd"
date: 2006-01-28
forum: Server Platforms
---

### Post by t0bb3 on 2006-01-28
Hi, How come the user "ftpfamily" can watch the content of the upload folder? I thought the "DenyUser ftpfamily" option would take care of that?

```
#VALID LOGINS
<Limit LOGIN>
	AllowUser ftpmp3
	AllowUser ftpt0bb3
	AllowUser ftpfamily
	DenyAll
</Limit>

<Directory /home/ftp/>
	HideNoAccess on

	<Limit READ DIR>
		AllowAll
		IgnoreHidden on
	</Limit>
	
	<Limit WRITE>
		AllowUser ftpt0bb3
		DenyAll
	</Limit>
</Directory>

<Directory /home/ftp/download/>
	<Limit ALL>
		AllowUser ftpt0bb3
		DenyAll
	</Limit>

	<Limit READ DIR>
		AllowAll
	</Limit>
</Directory>

<Directory /home/ftp/upload/>
	<Limit READ WRITE DIR>
		Order deny,allow
		AllowAll
		DenyUser ftpfamily
	</Limit>

	<Limit DELE RMD XRMD>
		AllowUser ftpt0bb3
		DenyAll
	</Limit>
</Directory> 

<Directory /home/ftp/mp3/>
	<Limit READ DIR>
		AllowAll
	</Limit>
	
	<Limit WRITE>
		AllowUser ftpt0bb3
		DenyAll
	</Limit>
</Directory>

<Directory /home/ftp/family/>	
	<Limit ALL WRITE>
		AllowUser ftpt0bb3
		AllowUser ftpfamily
		DenyAll
	</Limit>
</Directory>
```

ftpfamily can't upload or download anything from the upload folder, but I don't want it to even be alowed to see what's in there...

---

### Post by Horndog on 2006-01-28
If this was Apache you would have to put the  "DenyAll" on top of the wrapper.
I have no experience with proFTPd but I looks like the wrappers are designed the same.

---

### Post by t0bb3 on 2006-01-28
I'm not sure I understand how you mean. I tried this, but that didn't work :(
```
#VALID LOGINS
<Limit LOGIN>
	DenyAll
	AllowUser ftpmp3
	AllowUser ftpt0bb3
	AllowUser ftpfamily
</Limit>

<Directory /home/ftp/>
	HideNoAccess on

	<Limit READ DIR>
		AllowAll
		IgnoreHidden on
	</Limit>
	
	<Limit WRITE>
		DenyAll
		AllowUser ftpt0bb3
	</Limit>
</Directory>

<Directory /home/ftp/download/>
	<Limit ALL>
		DenyAll
		AllowUser ftpt0bb3
	</Limit>

	<Limit READ DIR>
		AllowAll
	</Limit>
</Directory>

<Directory /home/ftp/upload/>
	<Limit READ WRITE DIR>
		Order deny,allow
		AllowAll
		DenyUser ftpfamily
    </Limit>

	<Limit DELE RMD XRMD>
		DenyAll
		AllowUser ftpt0bb3
	</Limit>
</Directory> 

<Directory /home/ftp/mp3/>
	<Limit READ DIR>
		AllowAll
	</Limit>
	
	<Limit WRITE>
		DenyAll
		AllowUser ftpt0bb3
	</Limit>
</Directory>

<Directory /home/ftp/family/>	
	<Limit ALL WRITE>
		DenyAll
		AllowUser ftpt0bb3
		AllowUser ftpfamily
	</Limit>
</Directory>
```

---

### Post by Horndog on 2006-01-28
Try looking here for more ideas.

[http://www.proftpd.org/docs/example-conf.html]("http://www.proftpd.org/docs/example-conf.html")

---

### Post by t0bb3 on 2006-01-29
I really don't understand how this stuff works :(

With this everyone can log in, and everyone can write/delete stuff from anywhere in the ftp dirs
```
#VALID LOGINS
<Limit LOGIN>
	DenyAll
	AllowUser ftpmp3
	AllowUser ftpt0bb3
	AllowUser ftpfamily
</Limit>

<Directory /home/ftp>
	<Limit WRITE>
		AllowAll
	</Limit>
</Directory>
```


With this code everybody can log in, and ftpt0bb3 can write/delete from most directories, but not all. I could write/delete in those directories in the above example. Why can't I now?```
#VALID LOGINS
<Limit LOGIN>
	DenyAll
	AllowUser ftpmp3
	AllowUser ftpt0bb3
	AllowUser ftpfamily
</Limit>

<Directory /home/ftp>
	<Limit WRITE>
		DenyAll
		AllowUser ftpt0bb3
	</Limit>
</Directory>
```

With this code nobody can log in, not even ftpt0bb3. I get "PORT command failed, Operation not permitted". What's up with that?```
#VALID LOGINS
<Limit LOGIN>
	DenyAll
	AllowUser ftpmp3
	AllowUser ftpt0bb3
	AllowUser ftpfamily
</Limit>

<Limit ALL>
	DenyAll
</Limit>

<Directory /home/ftp>
	<Limit READ DIRS>
		AllowAll
	</Limit>
	
	<Limit WRITE>
		AllowUser ftpt0bb3
	</Limit>
</Directory>
```

If someone could please explain to me what is going on here I might be able to understand it enough to do the rest of the config on my own :)

Thanks

---

