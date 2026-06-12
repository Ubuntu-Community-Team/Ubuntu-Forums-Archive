---
title: "Rails / Gem Perimissions issue"
date: 2009-07-31
forum: Server Platforms
---

### Post by dave9191 on 2009-07-31
Hi guys, 

Im sorry if Im posting in the wrong category. 

I need a little help finishing off a Rails install. I installed everything I needed, instead of using sudo, I was using root. As far as I can tell everything is installed, but I have one problem.

The permissions are wrong. When I try to run 'rails' as non root I get a permission denied. And when I try to run 'gem as non root, I get : 

/usr/local/lib/site_ruby/1.8/rubygems.rb:8:in `require': no such file to load -- rubygems/defaults (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:8
        from /usr/bin/gem:8:in `require'
        from /usr/bin/gem:8


Could someone point me in the right direction as to how to start fixing the permission errors? 

Many thanks, 

--
Dave

---

