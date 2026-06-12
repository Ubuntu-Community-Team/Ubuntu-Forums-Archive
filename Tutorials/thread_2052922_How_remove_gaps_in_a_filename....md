---
title: "How remove gaps in a filename..."
date: 2012-09-04
forum: Tutorials
---

### Post by shantiq on 2012-09-04
remove gaps in a filename  for "_"   then for "nogap"   then for "." then for &#9668;&#9658;
===============================================================================


first cd to folder then ::

```
for f in *; 
do rename 's/\ * /_/g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * //g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * /./g'   "$f"  "${f%.*}.*" ;done
```

```
for f in *; 
do rename 's/\ * /&#9668;&#9658;/g'   "$f"  "${f%.*}.*" ;done
```

---

