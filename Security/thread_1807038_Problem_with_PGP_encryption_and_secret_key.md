---
title: "Problem with PGP encryption and secret key"
date: 2011-07-18
forum: Security
---

### Post by AndreyFS on 2011-07-18
Hello,
 
I have a problem using PGP encryption.
I am running Windows 7 operating system.
 
I have PGP working perfectly fine when running manually through DOS mode (cmd.exe):
gpg -ase --always-trust --batch --passphrase myphrase --output c:\testdir\testfile.csv.pgp -r someword c:\testdir\testfile.csv
 
Now the problem happens when I am trying to run same script in Perl in the browser (Perl + IIS are installed locally on my PC).
The error I am getting is: [COLOR=#000000][SIZE=3]gpg: no default secret key: No secret key gpg: [COLOR=#000000][SIZE=2]C:\\testdir\\testfile.csv: sign+encrypt failed: No secret key [/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=#000000][SIZE=3][COLOR=#000000][SIZE=2]From what I understand, the secret key is created under my user profile. IIS runs under some default user name, so it does not see the secret key.[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=#000000][SIZE=3][COLOR=#000000][SIZE=2]I am not sure how to solve this problem.[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=#000000][SIZE=3][COLOR=#000000][SIZE=2]Does anyone have an idea how to resolve this?[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=#000000][SIZE=3][COLOR=#000000][SIZE=2]Thank you,[/SIZE][/COLOR][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#000000][SIZE=2]-Andrey[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by spynappels on 2011-07-20
Ask in a Windows forum?

---

