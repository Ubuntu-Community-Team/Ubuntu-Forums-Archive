---
title: "TeX complaints..."
date: 2012-05-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by zika on 2012-05-14
```
Setting up texlive-extra-utils (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-font-utils (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-generic-extra (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-latex-extra (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-latex-extra-doc (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-pstricks (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-pstricks-doc (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-science (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Setting up texlive-science-doc (2011.20120509-1) ...


Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-extra.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-science.cfg

Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.

```Any quick remedy?

---

### Post by jfernyhough on 2012-05-14
Remove + reinstall?

--edit
Just happened to me... gah. Actually, does it matter? Looking at the line "Warning: These packages should be rebuild with tex-common." it implies it's a packaging thing, not anything wrong with our install. At least LyX is still outputting something that looks right...

---

### Post by codingman on 2012-05-14
eh... i use tex, no problems. don't think the problem of yours really matters.

---

### Post by zika on 2012-05-15
This does not in any way obscure my use of TeX but it could shed some light on possible problems later since there are:
-problems with (altered)directory structure...
```
:~$ gedit
ERROR   :Environment                   : /etc/texmf/texmf.cnf not found, using default search paths ['/usr/share/texmf-texlive', '/home/.../texmf'] (l.236)
```
-problems with configuration style location and structure (see above)...

---

