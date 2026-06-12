---
title: "SVN setup issues."
date: 2012-06-27
forum: Server Platforms
---

### Post by ajf412 on 2012-06-27
I'm getting close to getting this up and running.  I'd be pulling my hair out if I had any, but I bic my head...

My DDNS is obviously working, because it can see that I have a server up, but it wont put the SVN repository to the forefront!

[http://manateestudios.dlinkddns.com](http://manateestudios.dlinkddns.com) (or with https)
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

I'm thinking that SSL or SSH is getting in the way of having my SVN working?  I'm so new to this server stuff, so I'm lost as to what they do.

However, I do have WebDAV set up as per:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
>  <Location /svn/myproject>
     DAV svn
     SVNPath /home/svn/myproject
     AuthType Basic
     AuthName "myproject subversion repository"
     AuthUserFile /etc/subversion/passwd
     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
     LimitXMLRequestBody 0
  </Location>

I've been following two tutorials to get this set up:
[http://odyniec.net/articles/ubuntu-subversion-server/](http://odyniec.net/articles/ubuntu-subversion-server/)
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

Tortoise SVN on my Windows 7 PC says:
> Command  Checkout from [https://manateestudios.dlinkddns.com](https://manateestudios.dlinkddns.com), revision HEAD, Fully recursive, Externals included

Error  Unable to connect to a repository at URL

Any help would be GREATLY appreciated.

---

### Post by ajf412 on 2012-06-27
I'm thinking it must be something wrong with the ssl configuration that I set up from this link:  [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)
> NameVirtualHost *:443
<virtualhost *:443>
ServerAdmin webmaster@localhost

SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem

DocumentRoot /var/www/
<directory />
Options FollowSymLinks
AllowOverride None
</directory>

<directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
# Commented out for Ubuntu
#RedirectMatch ^/$ /apache2-default/
</directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<directory "/usr/lib/cgi-bin">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</directory>

ErrorLog /var/log/apache2/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined
ServerSignature On

Alias /doc/ "/usr/share/doc/"
<directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</directory>

</virtualhost>

Maybe something in there needs to be changed to my SVN directory at '/home/SVN/myproject'?

---

### Post by ajf412 on 2012-06-27
Okay, played around some, and now I have it detecting my main repository.  But now when I try to connect using TortoiseSVN from my PC via the internet, I get:
> error  redirect cycle detected for URL

Any ideas?

---

### Post by ajf412 on 2012-06-27
This is what I'm getting from TortoiseSVN:
> Checkout from [https://manateestudios.dlinkddns.com/svn/AfterMath](https://manateestudios.dlinkddns.com/svn/AfterMath), revision HEAD, Fully recursive, Externals included
[https://manateestudios.dlinkddns.com/svn/AfterMath](https://manateestudios.dlinkddns.com/svn/AfterMath)
[https://manateestudios.dlinkddns.com/svn/AfterMath](https://manateestudios.dlinkddns.com/svn/AfterMath)
Redirect cycle detected for URL
 'https://manateestudios.dlinkddns.com/svn/AfterMath'

And on these [forums]("http://www.svnforum.org/threads/40377-v1-7RC3-redirect-cycle-detected") I found:
> problem solved: I removed the symbolic links to the repository root in /var/www (there was a symlink from /var/www/repo to /svn/repo which is the base folder for my repositories). After removing the symlinks and restarting the httpd service, all worked fine.

So I went back, and I commented that portion out, which is also called for in the tutorial (I just didn't understand), but it still sends me through a redirect cycle.  =\

---

### Post by ajf412 on 2012-06-27
I found this at [http://svn.apache.org/repos/asf/subversion/trunk/subversion/libsvn_client/ra.c](http://svn.apache.org/repos/asf/subversion/trunk/subversion/libsvn_client/ra.c)

My programming skills are enough to get me understanding that this is what's sending me through redirects, but not why.  This isn't what's causing the redirects, but it's the symptom of whatever the problem is...

> #define SVN_CLIENT__MAX_REDIRECT_ATTEMPTS 3 /* ### TODO:  Make configurable. */

svn_error_t *
svn_client__open_ra_session_internal(svn_ra_session_t **ra_session,
                                     const char **corrected_url,
                                     const char *base_url,
                                     const char *base_dir_abspath,
                                     const apr_array_header_t *commit_items,
                                     svn_boolean_t use_admin,
                                     svn_boolean_t read_only_wc,
                                     svn_client_ctx_t *ctx,
                                     apr_pool_t *pool)
{
  svn_ra_callbacks2_t *cbtable;
  callback_baton_t *cb = apr_pcalloc(pool, sizeof(*cb));
  const char *uuid = NULL;

  SVN_ERR_ASSERT(base_dir_abspath != NULL || ! use_admin);
  SVN_ERR_ASSERT(base_dir_abspath == NULL
                        || svn_dirent_is_absolute(base_dir_abspath));

  SVN_ERR(svn_ra_create_callbacks(&cbtable, pool));
  cbtable->open_tmp_file = open_tmp_file;
  cbtable->get_wc_prop = use_admin ? get_wc_prop : NULL;
  cbtable->set_wc_prop = read_only_wc ? NULL : set_wc_prop;
  cbtable->push_wc_prop = commit_items ? push_wc_prop : NULL;
  cbtable->invalidate_wc_props = read_only_wc ? NULL : invalidate_wc_props;
  cbtable->auth_baton = ctx->auth_baton; /* new-style */
  cbtable->progress_func = ctx->progress_func;
  cbtable->progress_baton = ctx->progress_baton;
  cbtable->cancel_func = ctx->cancel_func ? cancel_callback : NULL;
  cbtable->get_client_string = get_client_string;
  cbtable->get_wc_contents = get_wc_contents;

  cb->base_dir_abspath = base_dir_abspath;
  cb->commit_items = commit_items;
  cb->ctx = ctx;

  if (base_dir_abspath)
    {
      svn_error_t *err = svn_wc__node_get_repos_info(NULL, &uuid, ctx->wc_ctx,
                                                     base_dir_abspath,
                                                     pool, pool);

      if (err && (err->apr_err == SVN_ERR_WC_NOT_WORKING_COPY
                  || err->apr_err == SVN_ERR_WC_PATH_NOT_FOUND
                  || err->apr_err == SVN_ERR_WC_UPGRADE_REQUIRED))
        {
          svn_error_clear(err);
          uuid = NULL;
        }
      else
        {
          SVN_ERR(err);
          cb->base_dir_isversioned = TRUE;
        }
    }

  /* If the caller allows for auto-following redirections, and the
     RA->open() call above reveals a CORRECTED_URL, try the new URL.
     We'll do this in a loop up to some maximum number follow-and-retry
     attempts.  */
  if (corrected_url)
    {
      apr_hash_t *attempted = apr_hash_make(pool);
      int attempts_left = SVN_CLIENT__MAX_REDIRECT_ATTEMPTS;

      *corrected_url = NULL;
      while (attempts_left--)
        {
          const char *corrected = NULL;

          /* Try to open the RA session.  If this is our last attempt,
             don't accept corrected URLs from the RA provider. */
          SVN_ERR(svn_ra_open4(ra_session,
                               attempts_left == 0 ? NULL : &corrected,
                               base_url, uuid, cbtable, cb, ctx->config, pool));

          /* No error and no corrected URL?  We're done here. */
          if (! corrected)
            break;

          /* Notify the user that a redirect is being followed. */
          if (ctx->notify_func2 != NULL)
            {
              svn_wc_notify_t *notify =
                svn_wc_create_notify_url(corrected,
                                         svn_wc_notify_url_redirect, pool);
              (*ctx->notify_func2)(ctx->notify_baton2, notify, pool);
            }

          /* Our caller will want to know what our final corrected URL was. */
          *corrected_url = corrected;

          /* Make sure we've not attempted this URL before. */
          if (apr_hash_get(attempted, corrected, APR_HASH_KEY_STRING))
            return svn_error_createf(SVN_ERR_CLIENT_CYCLE_DETECTED, NULL,
                                     _("Redirect cycle detected for URL '%s'"),
                                     corrected);

          /* Remember this CORRECTED_URL so we don't wind up in a loop. */
          apr_hash_set(attempted, corrected, APR_HASH_KEY_STRING, (void *)1);
          base_url = corrected;
        }
    }
  else
    {
      SVN_ERR(svn_ra_open4(ra_session, NULL, base_url,
                           uuid, cbtable, cb, ctx->config, pool));
    }

  return SVN_NO_ERROR;
}
#undef SVN_CLIENT__MAX_REDIRECT_ATTEMPTS

---

### Post by ajf412 on 2012-06-27
[https://discussion.dreamhost.com/thread-134221.html](https://discussion.dreamhost.com/thread-134221.html)
> RE: New svn repo causing "Redirect cycle detected for URL" error
[quote](02-14-2012 12:45 PM)roboshed Wrote:  
I did a little more experimenting and was able to create a (different) repo that worked, the only difference I found was that this time I didn't try to set up Trac along with svn, so maybe that was the issue.
If they were both subdirs of the same document root, that's likely the problem. Keep them separate:

/home/USER/trac.domain.com
/home/USER/svn.domain.com

not

/home/USER/domain.com/trac
/home/USER/domain.com/svn

If you don't like subdomains in your urls, there are ways to get around that, but you don't have to physically put them in the same dir to get:

[http://domain.com/trac](http://domain.com/trac)
[http://domain.com/svn](http://domain.com/svn)[/quote]

I don't think I've put 2 things in the same place, but it's possible.  I mean, I do get website language at [http://manateestudios.dlinkddns.com](http://manateestudios.dlinkddns.com)
and SVN language at [http://manateestudios.dlinkddns.com/svn/AfterMath](http://manateestudios.dlinkddns.com/svn/AfterMath)

Still working on it!

---

### Post by ajf412 on 2012-06-27
Okay, my repository is sending me to my repository in my reposity, that's sending me to a repository that's in my repository's repository?  But those don't even exist!
[https://manateestudios.dlinkddns.com/svn/AfterMath/AfterMath/](https://manateestudios.dlinkddns.com/svn/AfterMath/AfterMath/)
> This XML file does not appear to have any style information associated with it. The document tree is shown below.
<D:error xmlns:D="DAV:" xmlns:m="http://apache.org/dav/xmlns" xmlns:C="svn:">
<C:error/>
<m:human-readable errcode="2">Could not open the requested SVN filesystem</m:human-readable>
</D:error>

I have home > svn > AfterMath > empty

---

