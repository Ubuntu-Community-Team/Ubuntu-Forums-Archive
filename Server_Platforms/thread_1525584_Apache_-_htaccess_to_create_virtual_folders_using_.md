---
title: "Apache - htaccess to create virtual folders using rewrite or redirect?"
date: 2010-07-06
forum: Server Platforms
---

### Post by semmelbroesel on 2010-07-06
Hi.

After spending 3 frustrating hours trying to figure this out, it's time to ask for help...

I want to be able to give users their own "folder" on my site, e.g. [www.site.com/johnsmith/](www.site.com/johnsmith/) and [www.site.com/janedoe/](www.site.com/janedoe/) but I do not want these folders to be physically there or at least not physically in the www root folder.
There are files and folders that are in the www root folder that need to stay accessible.

The reason for this mess is that I don't want to end up having thousands of user folders all over the root of my server - I'd rather move them somewhere else and redirect them or something.

I played with .htaccess for a while, and I am getting close, but then either it doesn't work at all or creates an endless loop, and I don't understand why...

Here's a few examples I tried in .htaccess with many variations but without success:

```
Options +FollowSymlinks
RewriteEngine on

#RewriteCond   /%{REQUEST_URI} !-U
#RewriteRule   ^([a-z]+)          http://testsrv/test/$1

#RewriteCond   /%{REQUEST_FILENAME} !-f
#RewriteRule   ^([a-z]+) http://testsrv/test/$1

#RewriteCond /test/%{REQUEST_FILENAME}  -f
#RewriteRule ^(.*) /test/$1 [L]

#RewriteCond   %{REQUEST_URI} !-F
#RewriteRule   ^(.*) http://testsrv/test/$1 [R=404]

#RewriteCond %{REQUEST_FILENAME} !-f
#RewriteCond %{REQUEST_FILENAME} !-d
#RewriteRule ^.*$ /test/$1 [L]

```
I commented them all since neither of them seem to work. I always had one group of lines uncommented at a time.

What I got so far was that if a file name is entered, e.g. [www.site.com/testing.html](www.site.com/testing.html) that does not exist, but [www.site.com/test/testing.html](www.site.com/test/testing.html) does exist, then one of these examples worked, most others create URLs like [www.site.com/test/test/test/test/test/testing.html](www.site.com/test/test/test/test/test/testing.html) or similar or something that Firefox even refuses to show. I don't get where this loop is coming from, even after closing with [L] which should stop it...

Oh, in each user folder there will be an index.php file, and PHP is the language of choice on this server.

My first thought was to use the 404 default page, but then the 404 message is sent to the browser, too, and I can't transmit the original URL that was sent, so that doesn't work.

.htaccess seems to be my best guess, but I can't figure out why none of my examples work.

Is there any other possibility?
How do others solve this issue?

I would be perfectly happy to redirect the users to something like [www.site.com/users/johnsmith/](www.site.com/users/johnsmith/) - that would keep my root clean. The URL does not have to stay the same. I just has to redirect so I don't have to have these folders in root and still can give them an easy URL.

And no, I can't do something like [www.site.com/?johnsmith](www.site.com/?johnsmith) - that was vetoed by my boss (which I find annoying, but that's the way it is).

Thanks in advance!

---

### Post by semmelbroesel on 2010-07-07
After "sleeping on it", I realized I was missing a few pieces of information in my post...

On this site, I do have some valid folders that need to be excluded from redirecting, e.g. [www.site.com/site/index.php](www.site.com/site/index.php) etc., and I also need to exclude EXISTING files in the root level, eg. [www.site.com/index.php](www.site.com/index.php).

What I need to redirect are URLs like:
[www.site.com/thisuser](www.site.com/thisuser)
and
[www.site.com/thisuser/](www.site.com/thisuser/)
(allowing for user stupidity :-)  )

They should redirect (sorry, I should have been more precise before) to something like this:
[www.site.com/users/thisuser/index.php](www.site.com/users/thisuser/index.php)

Also forgot: Once this redirect has happened and the user is inside one of the excluded folders (users or site etc.), there should not be any further redirection - I keep reading things where once redirected the new URL keeps causing issues with redirect...

... and I also should mention (unless I already did) that the folders that the user will enter in their URLs do NOT physically exist in root, and I want to avoid 404 errors (since IE and Google Toolbar etc. will put in their own page then).

It does not matter to me if the browser still shows the old URL or the new one as long as a user can type the simple version and get to his page.

I kept trying a few more things I keep finding in forums, but all I keep getting are loops ([www.site.com/users/users/users/](www.site.com/users/users/users/)...), and I don't get why...

Again, any help would be greatly appreciated.

---

### Post by semmelbroesel on 2010-07-15
Problem solved.
I received an answer in another forum.

```

Options +FollowSymlinks
RewriteEngine on
RewriteCond $1 !^(newfolder|products|users|services)(/.*)?$
# RewriteCond $1 !\.(gif|jpe?g|png|ico|css|js|pdf|xml)$
RewriteCond %{SCRIPT_FILENAME} !-f
RewriteCond %{SCRIPT_FILENAME} !-d
RewriteRule ^([a-z0-9\_]+)/?$ /newfolder/index.php?id=$1 [R,QSA,L]

```

The first RewriteCond excludes folders that I know are always present on the server.
The second one can be ignored since I excluded periods in the Rule.
And at some point when I'm done testing, the [R] flag can go away since it creates a 302 redirect instead of a rewrite.

And I just got the additional advice:
To make a rule case-insensitive, use the [NC] or [NoCase] flag on the rule. This is 50% faster than using "[A-Za-z]" in the regex pattern.

Hopefully this may help someone else some day.

---

