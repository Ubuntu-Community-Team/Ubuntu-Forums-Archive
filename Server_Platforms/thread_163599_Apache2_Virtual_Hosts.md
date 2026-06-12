---
title: "Apache2 Virtual Hosts"
date: 2006-04-21
forum: Server Platforms
---

### Post by rensu on 2006-04-21
<VirtualHost *:80>
#1.#  ErrorDocument 401 /Error401.html
#2.#  ErrorDocument 404 /Error404.html
#3.#  RewriteEngine on
#4.#  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
#5.#  RewriteRule .* - [F]
</VirtualHost>

Can someone explain me those 5 lines? Can't understand what is it doing?:confused:

---

### Post by LordHunter317 on 2006-04-21
None of them are doing anything because they're commented out.

The first two rules specify custom pages for 404 and 401 errors.

The last three specify a rewrite rule: for requests of type TRACE or TRACK, the connection is forbidden.

---

### Post by rensu on 2006-04-22
I commented them out...
But are they needful?

---

### Post by peanut butter on 2006-04-22
i know the first two arent needed but it makes your error pages prettyer
i dont know what in the world the last three are but i've never had to use them. and my server has been up for about 3 months and no problem.
also a quick google search comes up with:
[http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fhttpd.apache.org%2Fdocs%2F2.0%2Fmod%2Fmod_rewrite.html&ei=OIVKRNrQJsSCYb72pOcH&sig2=who87XO_Muobzg9cfTHCrA](http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fhttpd.apache.org%2Fdocs%2F2.0%2Fmod%2Fmod_rewrite.html&ei=OIVKRNrQJsSCYb72pOcH&sig2=who87XO_Muobzg9cfTHCrA)

---

### Post by kmi on 2006-04-23
```
#3.# RewriteEngine on
#4.# RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
#5.# RewriteRule .* - [F]
```
These lines are here for security reasons to avoid cross-scripting attacks, they just act as explained in the above post.

[Cross site scripting]("http://en.wikipedia.org/wiki/Cross_Site_Scripting") according to Wikipedia.

---

