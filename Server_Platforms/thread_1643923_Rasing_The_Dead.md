---
title: "Rasing The Dead"
date: 2010-12-12
forum: Server Platforms
---

### Post by Vegan on 2010-12-12
Seems my server crapped out again, so I am restoring. So far so good but vhosts seems to be ill.

Suggestions

Listen 80

<VirtualHost _default_:*>
  DocumentRoot /var/www
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/chess
  ServerName chessmaster.tk
  ServerAlias [www.chessmaster.tk](www.chessmaster.tk)
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/developer
  ServerName contract-developer.tk
  ServerAlias [www.contract-developer.tk](www.contract-developer.tk)
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/econ
  ServerName global-econ.tk
  ServerAlias [www.global-econ.tk](www.global-econ.tk)
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/hardcore-games
  ServerName hardcore-games.tk
  ServerAlias [www.hardcore-games.tk](www.hardcore-games.tk)
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/vegan
  ServerName vegan-advocate.tk
  ServerAlias [www.vegan-advocate.tk](www.vegan-advocate.tk)
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot /www/windows-it
  ServerName windows-it.tk
  ServerAlias [www.windows-it.tk](www.windows-it.tk)
</VirtualHost>

---

