---
title: "Post your .emacs file."
date: 2011-07-12
forum: The Cafe
---

### Post by cgroza on 2011-07-12
I see that conky has a thread like this, lets see how many emacs users are around here.

Here is mine, learning emacs lisp and just wrote a few naive functions:

```


(setq make-backup-files nil) ; stop creating ~ files

;; line numbers
(require 'linum nil 'noerror)
(when (featurep 'linum)
  (global-linum-mode 1))
(add-hook 'python-mode-hook '(lambda () (define-key python-mode-map "\C-m" 'newline-and-indent)))
(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(c-default-style "gnu" t)
 '(c-special-indent-hook (quote (ignore)))
 '(column-number-mode t)
 '(inhibit-startup-screen nil)
 '(initial-buffer-choice nil))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 )

(defvar no-easy-keys-minor-mode-map (make-keymap) 
  "no-easy-keys-minor-mode keymap.")
(let ((f (lambda (m)
           `(lambda () (interactive) 
              (message (concat "No! use " ,m " instead."))))))
  (dolist (l '(("<left>" . "C-b") ("<right>" . "C-f") ("<up>" . "C-p")
               ("<down>" . "C-n")
               ("<C-left>" . "M-f") ("<C-right>" . "M-b") ("<C-up>" . "M-{")
               ("<C-down>" . "M-}")
               ("<M-left>" . "M-f") ("<M-right>" . "M-b") ("<M-up>" . "M-{")
               ("<M-down>" . "M-}")
               ("<delete>" . "C-d") ("<C-delete>" . "M-d")
               ("<M-delete>" . "M-d") ("<next>" . "C-v") ("<C-next>" . "M-x <")
               ("<prior>" . "M-v") ("<C-prior>" . "M-x >") 
               ("<home>" . "C-a") ("<C-home>" . "M->")
               ("<C-home>" . "M-<") ("<end>" . "C-e") ("<C-end>" . "M->")))
    (define-key no-easy-keys-minor-mode-map
      (read-kbd-macro (car l)) (funcall f (cdr l)))))
(define-minor-mode no-easy-keys-minor-mode
  "A minor mode that disables the arrow-keys, pg-up/down, delete
  and backspace."  t " no-easy-keys"
  'no-easy-keys-minor-mode-map :global t)
(no-easy-keys-minor-mode 1)


;; indentation
;; (setq-default c-basic-offset 4)
(setq c-default-style "linux"
          c-basic-offset 4)

(add-hook 'c-mode-common-hook
               '(lambda () (c-toggle-auto-state -1)))


;; personal hacks and functinos
(defun duplicate-line (lines)
  (interactive "p")
  (save-excursion
    (interactive) 
    (kill-line lines)
    (yank)
    (move-end-of-line 1)
;;    (newline)
;;    (next-line 1)
    (yank)
    (message "Line added to kill-ring.")
    )
  )



(defun copy-line (lines)
  (interactive "p")
  (kill-line lines)
  (yank)
  (message "Line added to kill-ring.")
)

(defun open-line-above (lines)
  (interactive "p")
  (save-excursion
    (move-beginning-of-line 1)
    (open-line lines)
    )
  )


(defun create-cpp-class (class-name)
  (interactive "MEnter class name: ")
  (let ((pb (point)) (pe nil))
       (newline)            
       ;; insert class text
       (insert "class " class-name)
       (newline)
       (insert "{")
       (newline)
       (insert "public:")
       (newline)
       (insert class-name "();")
       (newline)
       (insert "~" class-name "();")
       (newline)
       (insert "protected:")
       (newline)
       (insert "private:")
       (newline)
       (insert "};")
       (setq pe (point))
       (indent-region pb pe)
       )
  )

(defun create-header-guard (header-name)
  (interactive "MEnter header guard name: ")
  (newline)
  (beginning-of-buffer)
  (insert "#ifndef " header-name)
  (newline)
  (insert "#define " header-name)
  (newline)
  (newline)
  (end-of-buffer)
  (newline)
  (insert "#endif //" header-name)
 )

(defun insert-c-header (h-file)
  (interactive "MEnter header filename: ")
  (save-excursion
    (beginning-of-line)
    (insert "#include " h-file)
    (newline)
    )
  )

(defun create-c-block (block-sig)
  (interactive "MEnter block signature: ")
  (let ( (block-start (point)) (block-end nil) )
     (save-excursion
       (insert block-sig)
       (newline)
       (insert "{")
       (newline)
       (newline)
       (insert "}")
       (indent-region block-start (point))
       )
     )
    )

;; NOTE: C-c ... are all ours
(global-set-key "\C-cd" 'duplicate-line)
(global-set-key "\C-cc" 'copy-line)
(global-set-key "\C-co" 'open-line-above)
(global-set-key "\C-ct" 'create-cpp-class)
(global-set-key "\C-ch" 'create-header-guard)
(global-set-key "\C-ci" 'insert-c-header)
(global-set-key "\C-cb" 'create-c-block)

;; end ey bindings


;; end personal hacks and functions
(put 'narrow-to-region 'disabled nil)


```

---

### Post by Barrucadu on 2011-07-12
[.emacs](https://github.com/Barrucadu/home/blob/master/config/emacs) and [.emacs.d](https://github.com/Barrucadu/home/tree/master/config/emacs.d), I really need to tidy up my .emacs (and get around to properly learning elisp and writing some functions I've wanted for a long time now).

---

### Post by Dustin2128 on 2011-07-13
Haven't customized mine but I'm looking to write a .emacs file- what kind of stuff can you change?

---

### Post by matthew.ball on 2011-07-13
Cool, this looks like it could be promising!

I've been very lazy recently, but I will eventually get around to putting my config stuff on github (exactly like Barrucadu has done).

My .emacs is of a modest size (1.4k lines), so I don't think I should paste it *all* here, but if I use my [FONT="Courier New"]show-dot-files-structure[/FONT] function it returns:

```
70 matches for "^;;;+" in buffer: .emacs
      7:;;; user details
     13:;;; colour theme
     25:;;; common lisp
     30:;;; default function values
     45:;;; default variable values
     78:;;; default browser
     84:;;; default auto-mode list
    105:;;; default major mode
    111:;;; enable functions
    124:;;; custom variables
    133:;;; custom faces
    143:;;; global keyboard bindings
    186:;;; pretty lambdas
    192:;;; debugging
    197:;;; slime mode
    214:;;; stumpwm
    219:;;; antiword
    226:;;; package archiver
    235:;;; single line copy
    245:;;; single line cut
    255:;;; tramp
    261:;;; version control
    267:;;; backups
    280:;;; visual line mode
    285:;;; syntax highlighting
    296:;;; line numbers
    302:;;; save place in file
    309:;;; unique buffer names
    318:;;; recent files
    327:;;; bookmarks
    333:;;; yasnippet
    338:;;; smex
    344:;;; flyspell
    353:;;; ispell
    360:;;; ido
    453:;;; icomplete
    463:;;; ibuffer
    633:;;; minibuffer
    641:;;; save hooks
    646:;;; auto-insert
    651:;;; auto-complete
    682:;;; partial completion
    687:;;; auto-pair
    707:;;; compilation finish variable
    717:;;; calendar / diary
    752:;;; org-mode
    896:;;; eshell
    923:;;; mail (and mutt)
    940:;;; dired
   1002:;;; logic4fun
   1014:;;; javascript programming
   1019:;;; haskell programming
   1028:;;; c programming
   1053:;;; c# programming
   1058:;;; python programming
   1063:;;; LaTeX markup
   1220:;;; desktop save
   1247:;;; smart tab
   1269:;;; google functions
   1282:;;; word count function
   1305:;;; dot file structure
   1315:;;; bugs/fixes/todos
   1325:;;; switch to dot emacs
   1335:;;; startup message
   1342:;;; tip of the day
   1360:;;; evaluate and replace
   1373:;;; show parenthesis
   1385:;;; jump to matching parenthesis
   1395:;;; highlight special comments
   1401:;;; start emacs server
```
Which should give an idea of what I have used. If you see anything you're interested in, I can paste the appropriate section here.

Looking forward to seeing what others have done :)

Edit: Some cool stuff there cgroza, consider some of it stolen! :p

---

### Post by Queue29 on 2011-07-13
> **Dustin2128 said:**
> Haven't customized mine but I'm looking to write a .emacs file- what kind of stuff can you change?

Haha. *Anything*.  Your .emacs file is a bunch of emacs-lisp code. 

This right here is the key to any happy emacs user:

```

;; put autosave files (ie #foo#) and backup files (ie foo~) in ~/.emacs.d/.
(custom-set-variables
    '(auto-save-file-name-transforms '((".*" "~/.emacs.d/autosaves/\\1" t)))
      '(backup-directory-alist '((".*" . "~/.emacs.d/backups/"))))

;; create the autosave dir if necessary, since emacs won't.
;; (make-directory "~/.emacs.d/autosaves/" t)
;; (make-directory "~/.emacs.d/backups/" t)

```

I just make the directories by hand on any new machine but you can uncomment those two lines to do it for you.. every time emacs loads.

---

### Post by cgroza on 2011-07-13
> **Dustin2128 said:**
> Haven't customized mine but I'm looking to write a .emacs file- what kind of stuff can you change?
If you do something often, and a macro can't help you there, then throw in there a function and bind it to some key... C-cX shortcuts are all yours...

---

### Post by sujoy on 2011-07-13
Here's mine. [FONT="Courier New"]_[COLOR="Blue"][emacs.d at github]("https://github.com/binarycodes/dot.emacs")[/COLOR]_[/FONT]

> **Dustin2128 said:**
> Haven't customized mine but I'm looking to write a .emacs file- what kind of stuff can you change?

Umm, lets rather ask, "what kind of stuff can you NOT change?"

Answer: None that I know about :P

---

### Post by cgroza on 2011-07-13
> **sujoy said:**
> Here's mine. [FONT=Courier New]_[COLOR=Blue][emacs.d at github]("https://github.com/binarycodes/dot.emacs")[/COLOR]_[/FONT]



Umm, lets rather ask, "what kind of stuff can you NOT change?"

Answer: None that I know about :P
That is quite a collection... Mind if I borrow some?:P

---

### Post by sujoy on 2011-07-13
> **cgroza said:**
> That is quite a collection... Mind if I borrow some?:P

hack away with pleasure :guitar:

---

### Post by cgroza on 2011-07-16
anyone else?

---

### Post by matthew.ball on 2011-07-16
I finally put my config stuff on github actually: [here]("https://github.com/matthew-ball/config-scripts") is a link.

There's a bit more than just emacs there though.

---

### Post by etienne.mon on 2012-09-03
I am using emacs for latex here is my .emacs

```

;(iso-accents-mode t)
; Make Emacs UTF-8 compatible for both display and editing:
(prefer-coding-system 'utf-8)
(set-terminal-coding-system 'utf-8)
(set-keyboard-coding-system 'utf-8)

;;;;;;;;;;;;;;-----------------recent file--------------
    (require 'recentf)
    (recentf-mode 1)
(setq
  recentf-save-file "~/.emacs.d/cache/recentf"
  recentf-max-saved-items 100     ;; max save 100
  recentf-max-menu-items 15)      ;; max 15 in menu
(recentf-mode t)                  ;; turn it on

;;;----------------position fenetre pas de deplacement horizontale !---------
(setq default-frame-alist
      '((top  . 1) (right  . 300)
    (width . 100) (height . 75)
        (cursor-color . "white")
        (cursor-type . box)
        (font . "-*-Courier-normal-r-*-*-13-*-*-*-c-*-iso8859-1")))


;;;;----------------------------

(set-language-environment "UTF-8")

;;;-------pour mettre les sauvegarde de custom dans un fichier
(setq custom-file "~/.emacs.d/custom.el")
(load custom-file)



;;;;;;;
(setq truncate-partial-width-windows nil)


;;;;ajoute l'heure dans emac
(setq display-time-24hr-format t)
(display-time-mode t)

;;parentheses                                                                                                                                                                    
(show-paren-mode)

;; Afficher les numeros de colonnes et des lignes
(column-number-mode t)

;;put the line numbers on the left for a latex file
(line-number-mode t)
(add-hook 'find-file-hook (lambda () (linum-mode 1)))

;;; ------------------------ dictionnaire - correction orthographique -----------
(setq-default ispell-program-name "aspell")

(add-hook 'text-mode-hook
     (lambda ()
        (flyspell-mode 1)
        (ispell-change-dictionary "british")
        (turn-on-auto-fill)
))


;;;----------------raccourci lettre grec-------------------

;lettres grecques minuscules
(global-set-key [(meta a)] "\\alpha")
(global-set-key [(meta b)] "\\beta")
(global-set-key [(meta c)] "\\chi")
(global-set-key [(meta d)] "\\delta")
(global-set-key [(meta e)] "\\epsilon")
(global-set-key [(meta f)] "\\varphi")
(global-set-key [(meta g)] "\\gamma")
(global-set-key [(meta h)] "\\eta")
(global-set-key [(meta i)] "\\iota")
(global-set-key [(meta j)] "\\theta")
(global-set-key [(meta k)] "\\kappa")
(global-set-key [(meta l)] "\\lambda")
(global-set-key [(meta m)] "\\mu")
(global-set-key [(meta n)] "\\nu")
(global-set-key [(meta o)] "\\omega")
(global-set-key [(meta p)] "\\pi")
(global-set-key [(meta q)] "\\chi")
(global-set-key [(meta r)] "\\rho")
(global-set-key [(meta s)] "\\sigma")
(global-set-key [(meta t)] "\\tau")
(global-set-key [(meta u)] "\\upsilon")
(global-set-key [(meta y)] "\\xi")
(global-set-key [(meta z)] "\\zeta")
(global-set-key [(meta E)] "\\varepsilon")
(global-set-key [(meta v)] "\\varpi")



;lettres grecques majuscules

(global-set-key [(meta G)] "\\Gamma")
(global-set-key [(meta D)] "\\Delta")
(global-set-key [(meta F)] "\\Phi")
(global-set-key [(meta J)] "\\Psi")
(global-set-key [(meta L)] "\\Lambda")
(global-set-key [(meta O)] "\\Omega")
(global-set-key [(meta P)] "\\Pi")
(global-set-key [(meta T)] "\\Theta")
(global-set-key [(meta S)] "\\Sigma")
(global-set-key [(meta X)] "\\Xi")
(global-set-key [(meta U)] "\\Upsilon")



;math


(defun parentheses () (interactive)
         (insert "()") (forward-char -1))
(global-set-key "(" 'parentheses)

(defun accolades () (interactive)
         (insert "{}") (forward-char -1))
(global-set-key "{" 'accolades)

(defun crochets-d () (interactive)
         (insert "[]") (forward-char -1))
(global-set-key "[" 'crochets-d)

;(defun modemath () (interactive)
;        (insert "$$") (forward-char -1))
;(global-set-key "\C-$" 'modemath)


(defun souligne () (interactive)
         (insert "_{}") (forward-char -1))
(local-set-key "_" 'souligne)
;(global-set-key "_" 'souligne)

(defun surligne () (interactive)
         (insert "\\overline{}") (forward-char -1))
(global-set-key [(meta -)] 'surligne)

(defun underline () (interactive)
         (insert "\\underline{}") (forward-char -1))
(global-set-key [(meta _)] 'underline)

(defun puissance () (interactive)
         (insert "^{}") (forward-char -1))
(global-set-key "\C-^" 'puissance)

;(fset 'modemath [ space $ space  $ left delete left delete right ])
;(global-set-key '[(meta $)] 'modemath)






(defun mathcal () (interactive)
(insert "\\mathcal{}")(forward-char -1))
(global-set-key [(meta M)] 'mathcal)

(defun mathfrak () (interactive)
(insert "\\mathfrak{}")(forward-char -1))
(global-set-key [(meta     K)] 'mathfrak)

(defun ldots () (interactive)
(insert ", \\ldots ,"))
(global-set-key [(meta \.)] 'ldots)

(defun widetilde () (interactive)
(insert "\\widetilde{}")(forward-char -1))
(global-set-key [(\~)] 'widetilde)

(defun mbox () (interactive)
(insert "\\mbox{}")(forward-char -1))
(global-set-key [(meta B)] 'mbox)

(defun frac () (interactive)
(insert "\\frac{}{}")(forward-char -3))
(global-set-key [(meta /)] 'frac)




;;;; -------------------  Auctex --------------------------------------

;(add-hook 'LaTeX-mode-hook '(
;(load ~/.emacs.d/my-latex.el)
;)

;;    (setq TeX-auto-save t)
;;    (setq TeX-parse-self t)
;;    (setq-default TeX-master nil)

;;     (add-hook 'laTeX-mode-hook 'visual-line-mode)
;;         (add-hook 'laTeX-mode-hook 'flyspell-mode)
;;     (add-hook 'laTeX-mode-hook 'LaTeX-math-mode)
;;     (add-hook 'laTeX-mode-hook 'turn-on-reftex)
   
;;(setq reftex-plug-into-AUCTeX t)

;;(setq TeX-PDF-mode t)     ;;  Active le mode pdflatex par défaut
;;(setq TeX-auto-save t)
;;(setq TeX-parse-self t)


;; ------------------
;; POUR LATEX
;; ------------------

(add-hook 'LaTeX-mode-hook 'LaTeX-math-mode) ;;charge Latex-math-mode
(setq TeX-PDF-mode t)

;; definition de la touche F12 afin qu'elle insere une paire d'accolades
;; (utile pour les fichiers TeX)
;;(global-set-key [f12] 'tex-insert-braces)
;; (sous Xp) Décommenter la ligne suivante et
;; vérifier que Emacs utilise Aspell au lieu d'Ispell pour la correction
;; d'orthographe.
;;(setq-default ispell-program-name "c:/program files/aspell/bin/aspell.exe")
;; (sous Ubuntu) rien a faire.
;; Definir le dictionnaire francais par defaut (penser a installer le paquet
;; aspell-fr pour avoir le dictionnaire francais installe sous Ubuntu;
;; (sous Xp) il faut aussi telecharger ce dictionnaire
;;(setq-default ispell-global-dictionary "francais")
;;(setq-default ispell-extra-args '("--reverse"))
;; pour compiler directement avec la commande pdflatex
;;(setq TeX-PDF-mode t)
;; pour utiliser evince a la place de xpdf
;;(setq TeX-view-program-list '(("Evince" "evince --page-index=%(outpage) %o")))
;;(setq TeX-view-program-selection '((output-pdf "Evince")))
;; emacs en plein écran avec la touche F11
;;(defun toggle-fullscreen (&optional f)
;; (interactive)
;; (let ((current-value (frame-parameter nil 'fullscreen)))
;; (set-frame-parameter nil 'fullscreen
;; (if (equal 'fullboth current-value)
;; (    if (boundp 'old-fullscreen) old-fullscreen nil)
; (progn (setq old-fullscreen current-value)
; 'fullboth)))))
; (global-set-key [f11] 'toggle-fullscreen)
; ; Make new frames fullscreen by default. Note: this hook doesn't do
; ; anything to the initial frame if it's in your .emacs, since that file is
; ; read _after_ the initial frame is created.
; ; (add-hook 'after-make-frame-functions 'toggle-fullscreen)

(add-hook 'lateX-mode-hook
  '( (load-file "~/.emacs.d/my-latex.el")  ; load these LaTeX preferences
   ))
```

---

### Post by etienne.mon on 2012-09-03
Hello,

 I am struggeling with my .emacs file: I want that when I press "_" emacs write "_{ }".
So I write this in my .emacs file (see previous post)

(defun souligne () (interactive)
         (insert "_{}") (forward-char -1))
(global-set-key "_" 'souligne)

It does not work. What is strange is that if I put 
(defun souligne () (interactive)
         (insert "_{}") (forward-char -1))
(global-set-key "z" 'souligne)
when I press "z", emacs write "_{}" !!!

So in emacs, I try to M-x global-unset-key then _ but it does not work in emacs. the button _ still works !!!

I also wanted to press ^ and get ^{} and press $ and have $ $ but it not works !

Notice that for ( ) or {} it works fine

Anyone has an idea, it seems to me that these keys are protected ?

thx in advance
Etienne

---

### Post by etienne.mon on 2012-09-11
I solve my problem.
The major mode Latex-mode redefines some keys.
Here it is explain what you can do
[http://http://ergoemacs.org/emacs/reclaim_keybindings.html](http://http://ergoemacs.org/emacs/reclaim_keybindings.html)
Here is my new .emacs file

[B]defun parentheses () (interactive) (insert "()") (forward-char -1)) 
(defun modemath () (interactive)(insert "$$") (forward-char -1)) 
(defun souligne () (interactive)(insert "_{}") (forward-char -1)) 
(defun puissance () (interactive)(insert "^{}") (forward-char -1)) 

(add-hook 'LaTeX-mode-hook 
 (lambda () 
 (define-key  LaTeX-mode-map (kbd "(") 'parentheses) 
 (define-key  LaTeX-mode-map (kbd "$") 'modemath) 
 (define-key  LaTeX-mode-map (kbd "_") 'souligne) 
 (define-key  LaTeX-mode-map (kbd "^") 'puissance) 
) 
) [/B]

---

