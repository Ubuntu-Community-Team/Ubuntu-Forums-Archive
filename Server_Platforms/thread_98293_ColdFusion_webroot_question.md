---
title: "ColdFusion webroot question"
date: 2005-12-02
forum: Server Platforms
---

### Post by ytseshred on 2005-12-02
My goal is to be able to instantiate a ColdFusion component that is stored in a common components directory.

My webserver is Apache.

I have ColdFusion installed running through apache (not through Macromedia JRun).  I have an alias setup in apache2.conf which looks something like:

(where SITEURL is the url to my site from my base IP/domain)

```

Alias /SITEURL/ "/usr/local/sites/SITEURL/"
<Directory "/usr/local/sites/SITEURL/">
  Options Indexes MultiViews
  AllowOverride None
  Order allow,deny
  Allow from all
</Directory>

```

I want to use a ColdFusion component where I don't have to invoke it from the current directory that my .cfm file is in.  Specifically, if my site is at /SITEURL/ within that site, I want a folder at /SITEURL/comps/  that stores all my components that I can invoke methods on from any directory further into the site.

The ColdFusion documentation has a page called "Specifying the CFC Location", which says that ColdFusion searches directories in the following order when looking for a component:
1) Local directory
2) web root
3) Directories specified in the ColdFusion administrator.

I am guessing that there is a way to tell Apache that the /SITEURL/ folder has a webroot of /usr/local/sites/SITEURL/  so that I can invoke my components as such, within the .cfm pages:

```
<cfobject component="comps.component-name" name="myComponent">
```

Can anyone let me know if this is possible, and if so, what I need to modify within Apache to do this, instead of specifying specific directories within the ColdFusion administrator?

(I don't want to do it within the administrator, in case I want to have common component names in the future deployed across multiple coldfusion applications).

Thanks.

---

