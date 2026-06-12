---
title: "Disable Ciphers / TLS"
date: 2022-02-03
forum: Security
---

### Post by iamlearning on 2022-02-03
Hi folks,

I would like to disable certain ciphers (Eg. AES 256-bit key size OR shorter, Blowfish) and TLS/SSL (Eg. TLS version 1.1 and below / SSL 3 / SSL 2) in Ubuntu 16.04 and 18.04.
As I did some google in the internet, so far the resultz only show me on how to disable those ciphers/TLS on the application itself (Eg. SSH and web severs like apache).
As I am a Windows user, I understand that I am able to disable those ciphers/TLS _system-wide_ in windows by configuring on the registry.

May I know is there a way to disable certain ciphers and TLS/SSL _system-wide_ in Ubuntu 16.04 and 18.04 ?

Thanks in advance

---

### Post by TheFu on 2022-02-04
There isn't a central place to enable/disable these things. Each program has control over what they use or block.  Linux users like to have control.  There are different types of encryption. Symmetric and asymmetric are used for different needs.  You can look those up. Symmetric is typically used for things like HTTPS where lots and lots of data will be transferred and the usefulness of the data is for a very short period.  Asymmetric encryption is used for authentication - usually PKI.  This is where we need to make the brute-force solving of the problem impossible for the next 10,000+ years, regardless of computer performance doubling each year.

AES-256 is commonly used in browsers for HTTPS traffic, but AES-128 may be used, depending on the remote server.  I don't think you want to disable those.  The server is what needs to decide which level is used.  As an end-user, you probably can only specify the order that a cypher are requested, but the server and client can only chat using a cypher and key-type they both understand.  I know I've never touched the client-side settings for this, but have modified my server to block poor encryption modes.

For ssh, each connection uses the cypher you specify, provided the server isn't blocking it.  That is in the /etc/ssh/sshd_config file. The current default for 20.04 ssh certs are documented in the manpage:
> ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521, ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
Certificates signed using other algorithms will not be accepted for public key or host-based authentication.

There are also the types of accepted key types. Again, the manpage lists the defaults and how to specify those allowed. There is a command to get them too:
```
$ ssh -Q HostbasedAcceptedKeyTypes
```
When we create ssh-keys using ssh-keygen, we can specify the type of key to be created.  Any key is 10,000x more secure than using a password/passphrase, so definitely set those up and you might want to update all of the keys uses whenever you change OSes. Just be certain to carry over the prior key if you've disabled password-based authenication (which you should do) to remote systems.

So, I guess you'll be using that web search and manpages ...

---

### Post by iamlearning on 2022-02-05
Hi TheFu,

Thank you so much for the explanation with example.
The reason why I need to disable ciphers like AES128 is due to the security policy that was given to me. However, I have been googling about how to enable/disable those ciphers/TLS/SSL system-wide on ubuntu but I cant seems to find a solution. Solutions that I have found so far is only specific to respective application.

Based on what you have mentioned, seems like there is no way to configure to enable/disable ciphers/TLS/SSL system-wide, unlike Windows which can be configured at the registry to enable/disable system-wide. Enable/disable ciphers/TLS/SSL in Linux can only be configured at respective application end itself (Eg. SSH at sshd_[COLOR=#000000]config file, web server at their respective config file[/COLOR]), not OS level.

I am still trying to learn Linux. Thanks again for the explanation. =)

---

### Post by TheFu on 2022-02-05
>  I am still trying to learn Linux. Thanks again for the explanation. =) 
That will take more than a lifetime.  I've been at it since the early 1990s and figure I might know about 10%, if that. The learning curve is very steep, since you'll need to unlearn about 80% of what Windows teaches that just doesn't apply.

If you really want to learn Unix-like OSes, ignore the GUI. The GUI is not the OS, it is just another program.  Learn the CLI interface. With that, controlling 1 or 10,000 systems is nearly the same effort.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a fine introductory book, free to download without any hassle. I've used it in my Beginner Linux Classes.  The GUI is a 20% answer and no Unix server will have any GUI. Nearly all connectivity will be through ssh or ssh-based protocols.  If you use any other protocol, it should probably use an ssh-tunnel for the connection and the remote server should be setup NOT to allow connections from other hosts. All connections should appear from localhost.

Unix-like OSes are 90% the same and most follow the same (or very similar) security model. Some tack on extra security like AppArmor or SELinux or "Roles" which are a little different. Most use package manager, so you should never download a setup.exe file from anywhere. Going outside the package manager will lead to dependency issues.

BTW, I bet that Windows cannot control all ciphers centrally, so it is likely that whatever you are getting that isn't true. I can see where MSFT would make cipher services and have those controlled centrally (how else can MSFT MiTM stuff?), but that doesn't many every program installed will actually use the services.  

KNOWING that each impacted program on a system is handled is important.  I've worked in highly secure facilities. Most were air-gapped with no way to most people to get any code into the environment, including programmers. On those networks, MS-Windows wasn't allowed and users didn't have physical access to the cables, ports or connections to the systems.

---

