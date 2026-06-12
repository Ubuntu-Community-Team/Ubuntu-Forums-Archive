---
title: "OpenDNS encrypts all i/o me to server"
date: 2012-02-20
forum: Ubuntu Dev Link Forum
---

### Post by Mark_in_Hollywood on 2012-02-20
I have been using [OpenDNS]("https://www.opendns.com/") servers since 2008. Recently, OpenDNS started offering OpenDNS Crypt for Linux. It encrypts all traffic between my 'puter and their servers.

To use their DNSCrypt package the user must download a small file from here this [link]("https://blog.opendns.com/2012/02/16/tales-from-the-dnscrypt-linux-rising/"):

Once I had that downloaded, the Ubuntu Software Center offered the install routine. Yet, when I clicked the radio-button "Install" a warning message came back which talked about that package being badly written code. The message reads:

[COLOR="red"]The package is of bad quality - The installation of a package which violates the quality standres ins't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details, beneath.

Lintian check results for /home/mark/Downloads/dnscrypt-proxy_0.9_i386.deb:
Use of uninitialized value $ENV{"HOME"} in concatenation (.) or string at /usr/bin/lintian line 112.
E: dnscrypt-proxy: maintainer-name-missing <root@debian>
E: dnscrypt-proxy: maintainer-address-malformed <root@debian>[/COLOR]

I immediately posted about this at the Absolute Beginner Forum and after a few days, 117 views and NO responses.

I also posted the warning message at the OpenDNS forums. The [thread/post]("http://forums.opendns.com/comments.php?DiscussionID=13345&page=1#Item_0") is still quite short, being but 1 post and 4 responses.

I hope that URL will show the post, as I had to register and login at that Forum. The post title at the forum is:

[COLOR="Red"]DNSCrypt: Linux Rising Ubuntu SoftCtr says: Bad Quality & won't install[/COLOR]

After my post, I received two messages from that Forum. The first relevant one is:

[COLOR="Red"]The errors about the Debian package on Ubuntu can safely be ignored. 

If installing the package using the Ubuntu Software Center doesn't work, you can install it using the command line with "sudo dpkg -i dnscrypt-proxy_0.9_i386.deb".

The package just installs a new command (/usr/sbin/dnscrypt-proxy). It doesn't change anything to your network settings.
If you want to stop it, you can type sudo pkill dnscrypt-proxy[/COLOR]

and the second one is from a poster calling himself: maintenance and reads:

[COLOR="Red"]I'm unsure as to the cause of the first message, which does not, however, indicate "bad code" or "bad quality". It still works just fine, and all that is installed is a command binary which you must actually use for it to do anything.

"E: dnscrypt-proxy: maintainer-name-missing <root@debian>
E: dnscrypt-proxy: maintainer-address-malformed <root@debian>"

Well, the package doesn't come from Ubuntu or Debian upstream, does it? If you want that to be different, ask the upstream maintainers to adopt the code.[/COLOR]

So, dear sir, if you have stayed with me so far, is it possible to have the upstream maintainers adopt the code? Is it bad code? Someone said at the OpenDNS forum that after installing it, he lost all 'net connectivity. I don't want to re-install the OS and /home, so I would appreaciate a little help.

Thank you, Ubuntu Community.

---

### Post by Bachstelze on 2012-03-30
Those errors do not indicate bad code, only non-standard packaging, so there is nothing that indicates that the package is unsafe to install. If the software center refuses to install it, you can always to it from the command line as indicated.

(That said, I can't vow that it's safe either, as I don't know the code in question.)

*EDIT:* Woops, this is the dev link forum, so it's a rather old post... Wel, in case anyone runs into the same error...

---

