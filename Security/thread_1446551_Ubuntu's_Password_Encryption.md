---
title: "Ubuntu's Password Encryption"
date: 2010-04-04
forum: Security
---

### Post by lateralus01 on 2010-04-04
I'm having trouble figuring out what encryption algorithm Ubuntu uses for it's passwords; various places have said sha-512 but when I encrypt my password string with sha-512 it doesn't match.

I've created a user named test with a password "password" for this example:

```

mark@mark-laptop:~/John$ sudo cat /etc/shadow | grep test
test:$6$.R/mk/Uv$7b.9w/5W4exX3kGRPR5gC63fPEqgzEKyBRXogMJ.WANpszWvcB4z..PHDL3M4FXnBjlzpQJYzHXw92HUtwm3Y0:14703:0:99999:7:::

```

yet if I encrypt the phrase "password" with sha-512, various tools have given me the same result which is:
```

b109f3bbbc244eb82441917ed06d618b9008dd09b3befd1b5e07394c706a8bb980b1d7785e5976ec049b46df5f1326af5a2ea6d103fd07c95385ffab0cacbc86

```

here's the output for "password\n"
```

9151440965cf9c5e07f81eee6241c042a7b78e9bb2dd4f928a8f6da5e369cdffdd2b70c70663ee30d02115731d35f1ece5aad9b362aaa9850efa99e3d197212a

```

neither of these match the hash stored in /etc/shadow; what encryption algorithm is being used and where can I find a way to generate that hash?

Thanks,
Lateralus01

---

### Post by rookcifer on 2010-04-04
$6$ = sha-512.

EDIT:  You must keep in mind that SHA-512 is a HASH, not an encryption algorithm.  Since the /etc/shadow passwords are also encrypted, it is natural they wouldn't match the hashes.  I am not sure, however, what encryption algorithm is used.

---

### Post by lateralus01 on 2010-04-04
Nevermind, modified DES algorithm; perl will generate the hash for me:
```

$word = "password";
$pwd = "$6$.R/mk/Uv$7b.9w/5W4exX3kGRPR5gC63fPEqgzEKyBRXogMJ.WANpszWvcB4z..PHDL3M4FXnBjlzpQJYzHXw92HUtwm3Y0"
# I got $pwd from the shadow file
if (crypt($word, $pwd) ne $pwd) {
        die "Sorry...\n";
    }
    else {
        print "$word is the password!\n";
    }

```

---

### Post by Dayofswords on 2010-04-04
watcha up to...


(and DES?!, thats been broken hasnt it)

---

### Post by Bachstelze on 2010-04-04
> **Dayofswords said:**
> 
(and DES?!, thats been broken hasnt it)

As rookcifer said, $6$ at the beginning of the line indicates SHA-512 is used, not DES. See [font=monospace]man crypt[/font] for more details.

---

### Post by cdenley on 2010-04-04
If you generate two hashes for the same password, they won't match because because a random salt is used. If it were that simple to verify a password hash, then it wouldn't be very safe. When authenticating, the salt is added to the password before the hash is computed and compared. This makes it impractical to use pre-computed hashes to crack passwords, since there would be too many possible salt values you would need to compute for every single possible passphrase.

[COLOR="Red"]red[/COLOR]=salt
[COLOR="Blue"]blu[/COLOR]e=hash
[COLOR="SeaGreen"]green[/COLOR]=algorithm (6 = SHA-512, 1 = MD5)

```

cdenley@cdenley:~$ mkpasswd -m SHA-512 test
$[COLOR="SeaGreen"]6[/COLOR]$[COLOR="red"]EUEoZKNThDNKmfdb[/COLOR]$[COLOR="Blue"]3g5AuZFmWHCaDJDJq2GVPdLQ8CAOPdDUGFYTf.T7SMbgk9aK2fyoo5EQlAZhfW.SEs11S4GYLNxX/RR5yxFUy.[/COLOR]
cdenley@cdenley:~$ mkpasswd -m SHA-512 test
$[COLOR="SeaGreen"]6[/COLOR]$[COLOR="Red"]SWunIV3lT3K52WKw[/COLOR]$S[COLOR="blue"]psARBUReIAbJ0pd0r.aFi9yj9AtIww9NFSNkFKTQgDGGY0GRQPagwm9bdKn1dndJw3XSy5AB6zWQK/D82a5p.[/COLOR]
cdenley@cdenley:~$ mkpasswd -m SHA-512 test nonrandom
$[COLOR="SeaGreen"]6[/COLOR]$[COLOR="red"]nonrandom[/COLOR]$[COLOR="blue"]y6NEeles.nw6ECcrMVQCj5JjX1ahluaLkbNsl/XD1l4ViGm1prkjkATSeZCaLlS7wWulmgIq.OR4sh.QrTOqe/[/COLOR]
cdenley@cdenley:~$ mkpasswd -m SHA-512 test nonrandom
$[COLOR="SeaGreen"]6[/COLOR]$[COLOR="red"]nonrandom[/COLOR]$[COLOR="blue"]y6NEeles.nw6ECcrMVQCj5JjX1ahluaLkbNsl/XD1l4ViGm1prkjkATSeZCaLlS7wWulmgIq.OR4sh.QrTOqe/[/COLOR]

```

The SHA-512 algorithm used for password encryption is not the same as the algorithm used for SHA-512 checksums. The same goes for MD5.

To generate that same hash, you just need to use the same salt:
```

cdenley@cdenley:~$ mkpasswd -m SHA-512 password .R/mk/Uv
$6$.R/mk/Uv$7b.9w/5W4exX3kGRPR5gC63fPEqgzEKyBRXogMJ.WANpszWvcB4z..PHDL3M4FXnBjlzpQJYzHXw92HUtwm3Y0

```

---

### Post by sajalagarwal on 2010-07-22
cdenley
can you tell me where this very salt is present in ubuntu .

Since ubuntu has to compare the password afterwards also so it should store the salt somewhere or else the comparision is not possible.

---

### Post by cdenley on 2010-07-22
> **sajalagarwal said:**
> cdenley
can you tell me where this very salt is present in ubuntu .

Since ubuntu has to compare the password afterwards also so it should store the salt somewhere or else the comparision is not possible.

The password hashes (which include the salt as my previous post explained) are in /etc/shadow.
```

sudo getent shadow $USER

```
**DO NOT POST THAT OUTPUT**

---

### Post by mathgeek2000 on 2010-11-23
> **cdenley said:**
> The password hashes (which include the salt as my previous post explained) are in /etc/shadow.
```

sudo getent shadow $USER

```**DO NOT POST THAT OUTPUT**

Just to explain the format of /etc/shadow again, and the command above.
**sudo ***is needed because ***getent** [I]accesses 'shadow' which is root read only, others no access.
The variable [/I]**$USER**[I] is you, the currently logged in user.

The output is the line from /etc/shadow related to your account:
 <Username>:<encpwd>:....(other data). where <encpwd> is your encrypted password.

the format of <encpwd> is:
  $#$SALT$PWD_SALTED_HASH

On Ubuntu 10.04.1, the # is '6' and means a SHA-512 Hash was used.
You can test your password with:

mkpasswd -m SHA-512 <passwd> SALT  (w/o '$')
This should return the encrypted password, starting w/ '$6$'

 
[/I]

---

