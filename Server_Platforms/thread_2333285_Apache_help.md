---
title: "Apache help?"
date: 2016-08-08
forum: Server Platforms
---

### Post by DMCShep on 2016-08-08
I'm trying to convert from Nginx to Apache so I can use perl as a CGI source. My site structure is simple enough that it should be fairly straightforward, but I cannot seem to figure out how to pull this off. Essentially, on one domain, I want the images, docs, and videos subfolder to redirect to an external drive, while everything else maps to localhost on port 2368. I've tried messing around with this, and the best I can get is to redirect all traffic to the port number, ignoring my subdirectories.

Here's what I've got so far, a "work in progress" if you will. Extra error logging and index showing is purely for verification.

```
<VirtualHost *:80>
#       ProxyRequests off
        ProxyPass / http://127.0.0.1:2368/
        ProxyPassReverse / http:/127.0.0.1:2368/


        ErrorLog ${APACHE_LOG_DIR}/catch-all.error
        CustomLog ${APACHE_LOG_DIR}/catch-all.log combined


        SetEnvIf Request_URI "^/images/.*$" subdir_images
        CustomLog ${APACHE_LOG_DIR}/images.log common env=subdir_images


#       <Directory />
#               AllowOverride None
#       </Directory>


        <Location "/images">
                Alias "/mnt/ext1/site/images"
                Options +Indexes
        </Location>


        <DirectoryMatch "^/images/*$">
                Options +Indexes
        </DirectoryMatch>
</VirtualHost>

```

What I want is this:

[http://site/](http://site/) --> redirects to [http://localhost:2368/](http://localhost:2368/)
[http://site/images/file.jpg](http://site/images/file.jpg) --> redirects to /mnt/ext1/site/images/file.jpg
[http://site/docs/form.pdf](http://site/docs/form.pdf) --> redirects to /mnt/ext1/site/docs/form.pdf
[http://site/some_other_dir/some_other_page](http://site/some_other_dir/some_other_page) --> redirects to [http://localhost:2368/some_other_dir/some_other_page](http://localhost:2368/some_other_dir/some_other_page)

I also have Munin installed and want to put that under the subdirectory "munin", but haven't gotten that far yet.

I'm clearly doing something wrong, but I haven't found the right way to do this. Can someone provide an example config that meets my needs? I'm struggling to learn the "proper" way to do this with Apache and would be grateful for anything really. (Mostly why I run Nginx as I understand it better). Running Apache 2.4.23 on Ubuntu Xenial 16.04.

**EDIT:**
I'd also like to convert another server over to Apache, and it relies on a similar setup but throws this into the mix:

[http://site/sync](http://site/sync) --> redirects to [http://localhost:8384/](http://localhost:8384/)
[http://site/sync/subdir](http://site/sync/subdir) --> redirects to [http://localhost:8384/subdir](http://localhost:8384/subdir)

This is simple stuff, but I haven't had success with any similar examples on Google as of yet.

---

### Post by SeijiSensei on 2016-08-09
I usually use Alias plus a <Directory> stanza:

```

<VirtualHost *:80>
ServerName   www.example.com
[stuff]

Alias /images /mnt/ext1/site/images
<Directory "/mnt/ext1/site/images">
    Options +Indexes
</Directory>

[stuff]
</VirtualHost>

```

I have no idea what you're trying to do with all the redirects and such.  Do you have another instance of Apache listening on port 2368?  Why are you using ProxyPass at all? That's usually intended to forward URL requests on to a server behind the publicly-visible one.  

You seem to be making this much harder than it needs to be.

---

### Post by DMCShep on 2016-08-09
Should've mentioned that I'm running Ghost blog, which is at localhost:2368.

This doesn't work:
```

<VirtualHost *:80>
        ProxyRequests off
        ProxyPass / http://127.0.0.1:2368/
        ProxyPassReverse / http:/127.0.0.1:2368/


        Alias /images /mnt/ext1/site/images
        <Directory "/mnt/ext1/site/images">
                Options +Indexes
        </Directory>
</VirtualHost>

```

Images do not load, and looking at the URL's it's trying to load, they are now followed by a trailing slash for some reason. Thinking the Proxy stuff was overriding it, I tried this:

```
<VirtualHost *:80>
        #----- Images -----#
        Alias /images /mnt/ext1/site/images
        <Directory "/mnt/ext1/site/images">
                Options +Indexes
        </Directory>


        #----- Ghost -----#
        <Location "/">
#               Wasn't allowed here
#               ProxyRequests off
                ProxyPass http://127.0.0.1:2368/
                ProxyPassReverse http:/127.0.0.1:2368/
        </Location>
</VirtualHost>

```

Still no dice. The Ghost blog works fine, but again, images do not.

---

### Post by Graham_Willis on 2016-08-09
I don't know Ghost at all, but isn't it possible to configure the path to multimedia at its own side? And even if the response to the last question's negative, wouldn't be it simpler just to mount the resource wherever it should be seen?

---

### Post by DMCShep on 2016-08-09
> **Graham_Willis said:**
> I don't know Ghost at all, but isn't it possible to configure the path to multimedia at its own side? And even if the response to the last question's negative, wouldn't be it simpler just to mount the resource wherever it should be seen?I believe the answers are "no" and "no" respectively. Ghost runs as its own server with a localhost port number of 2368 and directly handles all requests as a result. It doesn't really exist on the file system like it would most other sites. As a result, in order to properly handle images, I need to redirect requests to it directly. That is, unless they are made to one of a certain set of folders, in which case I redirect to the external hard drive as the same path. Ghost doesn't have this in it's (admittedly very basic) configuration. I may later upgrade to Joomla, but at the moment, Ghost fits my needs.

/images --> becomes --> /mnt/ext1/site/images
/docs --> becomes --> /mnt/ext1/site/docs

Everything else is passed as a direct request to localhost:2368 with the subdirectories and parameters intact:

/some-blog-post --> becomes --> [http://localhost:2368/some-blog-post](http://localhost:2368/some-blog-post)
/ghost/content/1/ --> becomes --> [http://localhost:2368/ghost/content/1/](http://localhost:2368/ghost/content/1/)
/catch-all --> becomes --> [http://localhost:2368/catch-all](http://localhost:2368/catch-all)

Maybe I'm reinventing the wheel here, but it sounds like a fairly simple use case for Apache to handle, I just can't figure out how to pull it off.

---

