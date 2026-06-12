---
title: "Newbie question about lighttpd (and rails)"
date: 2006-09-30
forum: Server Platforms
---

### Post by mwob on 2006-09-30
Hi all,

I'm so used to IIS in windows that I feed compltely stupid when it comes to anything else! I think I am being thick, but I can't work out how to use lighttpd to create a development environment to try rails.

Im IIS, you usually start from localhost, so if I have a testwebapp, I'll goto localhost/testwebapp and there it is. It looks like in ligthtpd that you instead have to specify a URL that lighttpd will instead redirect to your local website. Anyway, I have set-up my lighttpd.cofnig file with my new rails application. The snippet from the config file looks like this:

$HTTP["host"] == "rails.matttest.net" {
server.document-root = "/home/matt/railscode/matttest/public/"
server.error-handler-404 = "/dispatch.fcgi"
server.indexfiles = ("dispatch.fcgi")
 fastcgi.server = (".fcgi" =>
   ("localhost" =>
      ("socket" => "/tmp/railsapp.socket",
             	   "min-procs" => 2,
		   "max-procs" => 2,
	"bin-path" => "/home/matt/railscode/matttest/public/dispatch.fcgi",
	"bin-environment" => ("RAILS_ENV" => "development")
  )))
}

So, I restart lighttpd which doens't complain, and I am expecting now that I can open up firefox and goto "rails.matttest.net" and that should take me to my newly created rails web applicatioon... it doesn't! Instead it just hangs (firefox just stays stuck on "loading".... I can't do anything else)

Am I missing something obvious here? I'd really appreciate if someone could explain the basics to me!

Many thanks

Matt.

---

