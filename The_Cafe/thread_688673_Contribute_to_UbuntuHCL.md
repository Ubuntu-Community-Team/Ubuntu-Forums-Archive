---
title: "Contribute to UbuntuHCL"
date: 2008-02-05
forum: The Cafe
---

### Post by samb0057 on 2008-02-05
UbuntuHCL.org has been around since August, and has grown tremendously in the meantime, but we can always use some more reviews (the last couple of weeks have been pretty slow; not for visitors, but only reviews for some reason).

We have had 5200 unique visitors (not hits, not visits, but real unique visitors) in 2008. Over 850 of these unique visitors in February alone, and it's only the 5th!
Visitor base is growing but we still need a push to fill our database with useful reviews! Remember, the more reviews, the more search engine referrals, which means more visitors and in turn more reviews! We just need that push to get us to the point where the site is getting reviews every day.

We are also redoing our site to include enhancements on the current features, and new features. We are looking to eventually turn UbuntuHCL into a full community site. You can see our new development site at [http://dev.athertek.com/stage/ubuntuhcl/](http://dev.athertek.com/stage/ubuntuhcl/)

---

### Post by aaaantoine on 2008-02-05
There's a bug when I sign up at the dev site:

```

Unknown column 'deleted' in 'where clause'

#0 /home/atherdev/stage/ubuntuhcl/includes/functions/db/query.function.php(10): error::go('Unknown column ...')
#1 /home/atherdev/stage/ubuntuhcl/includes/functions/db/getRowsByConditions.function.php(6): db::query('SELECT 1 FROM `...')
#2 /home/atherdev/stage/ubuntuhcl/includes/functions/db/existsByConditions.function.php(6): db::getRowsByConditions('users', '`username` = "a...')
#3 /home/atherdev/stage/ubuntuhcl/includes/functions/db/existsByFields.function.php(6): db::existsByConditions('users', '`username` = "a...')
#4 /home/atherdev/stage/ubuntuhcl/actions/user/ex-signup.action.php(36): db::existsByFields('users', Array)
#5 /home/atherdev/stage/ubuntuhcl/includes/functions/std/include/includeFile.function.php(9): require('/home/atherdev/...')
#6 /home/atherdev/stage/ubuntuhcl/includes/functions/std/include/outputFile.function.php(8): std::includeFile('actions/user/ex...', Array)
#7 /home/atherdev/stage/ubuntuhcl/includes/functions/actions/execute.function.php(6): std::outputFile('actions/user/ex...')
#8 /home/atherdev/stage/ubuntuhcl/execute.php(20): actions::execute('user/ex-signup')
#9 /home/atherdev/stage/ubuntuhcl/includes/functions/std/include/includeFile.function.php(9): require('/home/atherdev/...')
#10 /home/atherdev/stage/ubuntuhcl/includes/functions/std/include/executeFile.function.php(8): std::includeFile('execute.php', Array)
#11 /home/atherdev/stage/ubuntuhcl/go.php(60): std::executeFile('execute.php')
#12 /home/atherdev/stage/ubuntuhcl/prepare.php(11): require('/home/atherdev/...')
#13 /home/atherdev/stage/ubuntuhcl/www/index.php(3): require('/home/atherdev/...')
#14 {main}

```

But anyway, I went ahead and registered at the main site, and submitted a review of my laptop.

---

### Post by hellion0 on 2008-02-05
> **aaaantoine said:**
> There's a bug when I sign up at the dev site:

*lots of text inside code tags*I had the same exact error a minute or two ago.

---

