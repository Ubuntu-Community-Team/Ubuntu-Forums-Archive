---
title: "python3.5 venv activate.fish error"
date: 2016-04-18
forum: Ubuntu Development Version
---

### Post by tuga3d on 2016-04-18
hi all, the activate.fish script of python3.5 venv has 2 errors in lines 58, 59:

```
    function fish_prompt
        # Prompt override?
->        if test -n "$__VENV_PROMPT__"
->            printf "%s%s%s" "$__VENV_PROMPT__" (set_color normal) (_old_fish_prompt)
            return
        end
```

should be:

 ```
   function fish_prompt
        # Prompt override?
        if test -n "__VENV_PROMPT__"
            printf "%s%s%s" "__VENV_PROMPT__" (set_color normal) (_old_fish_prompt)
            return
        end

```

---

