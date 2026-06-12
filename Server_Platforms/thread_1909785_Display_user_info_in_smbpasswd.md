---
title: "Display user info in smbpasswd?"
date: 2012-01-15
forum: Server Platforms
---

### Post by o0TarZan0o on 2012-01-15
My opinion, following command:

```
smbpasswd -a <username>
```

won't create a smbpasswd file in /etc/samba or anywhere else, so there is little problem here. How many users we added in "smbpasswd" file? What users we added into this file?

---

### Post by Toz on 2012-01-20
If you:
```
cat /etc/samba/smb.conf | grep passdb
```
...you should notice that the backend being used is tdbsam.

On my install (11.10), the password file is located at: /var/lib/samba/passdb.tdb. To view the contents of this file, you can either user the "strings" command or "tdbdump" (requires installation of "tdb-tools"):
```

sudo strings /var/lib/samba/passdb.tdb
sudo tdbdump /var/lib/samba/passdb.tdb

```

To view the users already setup, you could grep the above commands with USER_ to get a cleaner output:
```

sudo strings /var/lib/samba/passdb.tdb | grep USER_
sudo tdbdump /var/lib/samba/passdb.tdb | grep USER_

```

---

### Post by capscrew on 2012-01-20
> **Toz said:**
> If you:
```
cat /etc/samba/smb.conf | grep passdb
```
...you should notice that the backend being used is tdbsam.

On my install (11.10), the password file is located at: /var/lib/samba/passdb.tdb. To view the contents of this file, you can either user the "strings" command or "tdbdump" (requires installation of "tdb-tools"):
```

sudo strings /var/lib/samba/passdb.tdb
sudo tdbdump /var/lib/samba/passdb.tdb

```

To view the users already setup, you could grep the above commands with USER_ to get a cleaner output:
```

sudo strings /var/lib/samba/passdb.tdb | grep USER_
sudo tdbdump /var/lib/samba/passdb.tdb | grep USER_

```

To display all that is in the database use ```
sudo pdbedit -L
```

---

