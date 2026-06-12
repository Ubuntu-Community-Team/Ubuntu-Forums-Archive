---
title: "HELP: metasploit - ruby-openssl library not installed"
date: 2010-04-20
forum: Security
---

### Post by jfernandez1977 on 2010-04-20
Hi,

I'm new to metasploit.  I just installed it by following steps in [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

but when I run "msfconsole", I got the following error messages telling me that ruby-openssl is not installed.  I installed it "apt-get install libopenssl-ruby" but same message still comes again.  I'm running Ubuntu 9.10.  Can anybody with experience help?  Thanks very much.


JF


root@qa-ud910-32-1:/opt/metasploit3/msf3/external/ruby-lorcon2# msfconsole
*** The ruby-openssl library is not installed, many features will be disabled!
*** Examples: Meterpreter, SSL Sockets, SMB/NTLM Authentication, and more
[-] ***
[-] * WARNING: No OpenSSL support. This is required by meterpreter payloads and many exploits
[-] * Please install the ruby-openssl package (apt-get install libopenssl-ruby on Debian/Ubuntu
[-] ***
[*] WARNING! The following modules could not be loaded!

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

---

### Post by cariboo on 2010-04-20
I'm running Lucid, and there are three ruby-openssl libraries available, did you install the right one?

---

### Post by jfernandez1977 on 2010-04-21
thanks [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") for the reply.

I've only installed libopenssl-ruby

sudo apt-get install ruby libopenssl-ruby libyaml-ruby libdl-ruby libiconv-ruby libreadline-ruby irb ri rubygems

What are the other two?


JF[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")

---

### Post by cariboo on 2010-04-21
[list]
[*]libopenssl-ruby1.9
[*]libopenssl-ruby1.9.1
[/list]

---

### Post by shebaw on 2010-04-22
> **jfernandez1977 said:**
> Hi,

I'm new to metasploit.  I just installed it by following steps in [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

but when I run "msfconsole", I got the following error messages telling me that ruby-openssl is not installed.  I installed it "apt-get install libopenssl-ruby" but same message still comes again.  I'm running Ubuntu 9.10.  Can anybody with experience help?  Thanks very much.


JF


root@qa-ud910-32-1:/opt/metasploit3/msf3/external/ruby-lorcon2# msfconsole
*** The ruby-openssl library is not installed, many features will be disabled!
*** Examples: Meterpreter, SSL Sockets, SMB/NTLM Authentication, and more
[-] ***
[-] * WARNING: No OpenSSL support. This is required by meterpreter payloads and many exploits
[-] * Please install the ruby-openssl package (apt-get install libopenssl-ruby on Debian/Ubuntu
[-] ***
[*] WARNING! The following modules could not be loaded!

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl


Weird, I've don't remember installing any ruby library to make metasploit work. If the other libraries don't work, then try reinstalling it.

---

### Post by jfernandez1977 on 2010-04-22
thanks [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104").

I installed ruby-openssl1.9 and 1.9.1 but still getting the same message before.

$ msfconsole
*** The ruby-openssl library is not installed, many features will be disabled!
*** Examples: Meterpreter, SSL Sockets, SMB/NTLM Authentication, and more
[-] ***
[-] * WARNING: No OpenSSL support. This is required by meterpreter payloads and many exploits
[-] * Please install the ruby-openssl package (apt-get install libopenssl-ruby on Debian/Ubuntu
[-] ***
[*] WARNING! The following modules could not be loaded!

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: /opt/metasploit3/msf3/modules/auxiliary/scanner/ssh/ssh_login_pubkey.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/x64/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/meterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: /opt/metasploit3/msf3/modules/payloads/stages/windows/patchupmeterpreter.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/windows/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/bsd/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_bind_tcp.rb: MissingSourceFile no such file to load -- openssl

        /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: /opt/metasploit3/msf3/modules/payloads/singles/linux/x86/metsvc_reverse_tcp.rb: MissingSourceFile no such file to load -- openssl

---

### Post by risko on 2010-09-16
I've done the same thing and the same error happens to me too.
Did anyone find the solution?


risko@syntax:~/Transferências/msf3$ ./msfconsole 
*** The ruby-openssl library is not installed, many features will be disabled!
*** Examples: Meterpreter, SSL Sockets, SMB/NTLM Authentication, and more
/home/risko/Transferências/msf3/lib/rex/zip.rb:11:in `require': no such file to load -- zlib (LoadError)
	from /home/risko/Transferências/msf3/lib/rex/zip.rb:11
	from /home/risko/Transferências/msf3/lib/msf/util/exe.rb:23:in `require'
	from /home/risko/Transferências/msf3/lib/msf/util/exe.rb:23
	from /home/risko/Transferências/msf3/lib/msf/util.rb:22:in `require'
	from /home/risko/Transferências/msf3/lib/msf/util.rb:22
	from /home/risko/Transferências/msf3/lib/msf/core/framework.rb:2:in `require'
	from /home/risko/Transferências/msf3/lib/msf/core/framework.rb:2
	from /home/risko/Transferências/msf3/lib/msf/core.rb:33:in `require'
	from /home/risko/Transferências/msf3/lib/msf/core.rb:33
	from /home/risko/Transferências/msf3/lib/msf/ui/console/driver.rb:1:in `require'
	from /home/risko/Transferências/msf3/lib/msf/ui/console/driver.rb:1
	from /home/risko/Transferências/msf3/lib/msf/ui/console.rb:10:in `require'
	from /home/risko/Transferências/msf3/lib/msf/ui/console.rb:10
	from /home/risko/Transferências/msf3/lib/msf/ui.rb:10:in `require'
	from /home/risko/Transferências/msf3/lib/msf/ui.rb:10
	from ./msfconsole:96:in `require'
	from ./msfconsole:96

---

### Post by nlitsme on 2012-08-28
i had a similar problem with macports, first i had a problem building ruby, it complained about the directory 'openssl' already existing... i ignored that error, and tried install again, which then seemed to succeed.

then metasploit complained about openssl not being installed.

so now i retried building ruby, but now with paralel make disabled.

that solved the problem, like this:

```
sudo port install ruby19 build.jobs=1 +nosuffix

```

maybe ruby on ubunty has a similar problem?

---

### Post by overdrank on 2012-08-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

