---
title: "Lisp/Scheme Help"
date: 2008-12-03
forum: The Cafe
---

### Post by subaruwrc01 on 2008-12-03
I'm working on a project for my CSci class.  They created a game of Connect 4 for us, and we have to create a player.  However, the Connect Four they created allows you to drop from the left, or the top.  This is using MIT Scheme.  I was wondering if someone could direct me to some scheme help sites, or help debug my code.

Here is the code of the game (I cannot modify):
```
;;;; c4.scm

;;;;

;;;; Connect 4

;;;;

;;;; Written by Aaren Heroff



(define player-procedure '())

(define play-game

  ;; playerx should be 'human or string describing file containing player procedure

  (lambda (player1-file player2-file) 

    

    ;;; Defined constants

    (define *NUM-ROWS* 6)

    (define *NUM-COLUMNS* 7)

	

    (define *PLAYER-1-SYMBOL* 'x)

    (define *PLAYER-2-SYMBOL* 'o)

    (define *EMPTY-SYMBOL* '())

    

    (define *INVALID-MOVE-FORM-STRING* "Invalid position specified.")

    (define *CANNOT-MOVE-STRING* "Cannot move to specified position.")

    (define *ROW-PROMPT*    "Select side (0-left, 1-top): ")

    (define *COLUMN-PROMPT* "Select row: ")



    (define *PLAYER-1-PROMPT* "Player 1's Turn (X)")

    (define *PLAYER-2-PROMPT* "Player 2's Turn (O)")

    

    (define *GAME-OVER-INVALID-MOVE*    "Invalid move returned by player procedure.")

    (define *GAME-OVER-TIE-STRING*      "Game over: Game ends in tie.")

    (define *GAME-OVER-PLAYER-1-STRING* "Game over: Player 1 (X) wins.")

    (define *GAME-OVER-PLAYER-2-STRING* "Game over: Player 2 (0) wins.")



    (define *SLEEP-MILLISECONDS* 0)

    (define *STALL* #t)



    (define *WAIT-PROMPT*    "Hit enter to continue:")


	(define *ALL-MOVES* '((list 0 0) (list 0 1) (list 0 2) (list 0 3) (list 0 4) (list 0 5) (list 0 6)
                          (list 1 0) (list 2 0) (list 3 0) (list 4 0) (list 5 0)))
    (define *MAIN-DIAG* (list (list 2 0) (list 1 0) (list 0 0) (list 0 1) (list 0 2) (list 0 3)))
	(define *COUNTER-DIAG* (list (list 3 0) (list 4 0) (list 5 0) (list 5 1) (list 5 2) (list 5 3)))



    ;; Gets the player symbol for the other player

    (define other-player

      (lambda (player-symbol)

	(if (eq? player-symbol *PLAYER-1-SYMBOL*) *PLAYER-2-SYMBOL* *PLAYER-1-SYMBOL*)))

    

    ;; Gets the prompt string for the given player

    (define prompt-string

      (lambda (player-symbol)

	(if (eq? player-symbol *PLAYER-1-SYMBOL*) *PLAYER-1-PROMPT* *PLAYER-2-PROMPT*)))



    ;; Gets the winner string for the player-symbol or 'tie

    (define winner-string

      (lambda (winner)

	(cond ((eq? winner 'tie) *GAME-OVER-TIE-STRING*)

	      ((eq? winner *PLAYER-1-SYMBOL*) *GAME-OVER-PLAYER-1-STRING*)

	      (else *GAME-OVER-PLAYER-2-STRING*))))

                    

    ;;; Position abstraction

    

    ;; Position constructor

    (define make-position 

      (lambda (row column)

	(list row column)))

      

    ;; Row accessor

    (define get-row 

      (lambda (move)

	(car move)))

    

    ;; Column accessor

    (define get-column 

      (lambda (move)

	(cadr move)))

    

    ;; Does the given move have a valid form

    (define valid-position?

      (lambda (inputPosition)
       (let ((position (input->position inputposition)))

	(let ((integer<=? (lambda (x n) (and (integer? x) (< -1 x n)))))

	  (and (list? position) (= 2 (length position))

	       (integer<=? (get-row position) *NUM-ROWS*)

	       (integer<=? (get-column position) *NUM-COLUMNS*))))))


    

    ;;; Board abstraction



    ;; Sets a position on the board

   (define set-position!

  (lambda (position value board)

	(let ((pos (input->position position)))
	  (if (eq? (car position) 0)
           (set-car! (list-tail (list-ref board (cadr position)) 
               (+ (get-deepest-pos (positions->sym-lst (get-line-positions pos 3) board))1)) value)

	  (if (eq? (car position) 1) 
	       (set-car! (list-tail (list-ref board 
	          (+(get-deepest-pos (positions->sym-lst (get-line-positions pos 5) board))1)) (cadr position)) value))))))



    ;; Gets the value of the board at a given position

    (define get-position

     (lambda (position board)

	   (list-ref (list-ref board (get-row position)) (get-column position))))



    

    ;; Builds new board

    (define make-new-board

      (lambda ()

	(let ((board (repeat (repeat *EMPTY-SYMBOL* *NUM-COLUMNS*) *NUM-ROWS*)))

	  board)))

    

    ;;; Utilitiy procedures
    
    ;; converts a list of positions into their respective symbols
(define positions->sym-lst
  (lambda (position-lst board)
    (let ((sym-list '()))
      (for-each (lambda (position) 
                 (set! sym-list (append sym-list (list (get-position position board))))) position-lst)
                  sym-list)))

    
    ;;returns a copy of the row
(define select-row
  (lambda (row board)
    (positions->sym-lst (cons (list row 0) (get-line-positions (list row 0) 3)) board)))

(define select-column
  (lambda (col board)
    (positions->sym-lst (cons (list 0 col) (get-line-positions (list 0 col) 5)) board)))

(define select-diag
  (lambda (diag board)
    (positions->sym-lst (cons (list-ref *MAIN-DIAG* diag) (get-line-positions (list-ref *MAIN-DIAG* diag) 4)) board)))
    
(define select-counter-diag
  (lambda (diag board)
    (positions->sym-lst (cons (list-ref *COUNTER-DIAG* diag) (get-line-positions (list-ref *COUNTER-DIAG* diag) 2)) board)))

;;returns the "deepest *EMPTY-SYMBOL* in the lst, -1 if none
(define get-deepest-pos
  (lambda (lst)
     (let ((count -1) (stillEmptySym #t))
       (for-each (lambda (element)
                   (if stillEmptySym
                         (if (eq? element *EMPTY-SYMBOL*) (set! count (+ count 1))
                                                    (set! stillEmptySym #f))))
       lst)
       count)))
;;counts how many symbols are in a row
(define sym-count
  (lambda (symbol lst)
    (let ((runSum 0) (sumMax 0))
      (for-each (lambda (el) 
                      (if (eq? el symbol)
                          (set! runSum (+ runSum 1))
                          (if (> runSum sumMax) (begin (set! sumMax runSum)
                                                       (set! runSum 0))
                              (set! runSum 0)))) lst)
      (if (> runSum sumMax) runSum sumMax))))
    
    ;;converts input to the board coordinate equiv
  (define input->position
    (lambda (inputPosition)
     (let ((position '()))
       (if (eq? (car inputPosition) 0) (set! position (list (cadr inputPosition) 0)))
       (if (eq? (car inputPosition) 1) (set! position (list 0 (cadr inputPosition))))
       position)))
    
;;converts a position into the proper-input form. 
;;only valid on lists of the form (0 n) or (n 0)
  (define position->input
    (lambda (graphPosition)
      (let ((input '()))
        (if (eq? (cadr graphPosition) 0) (set! input (list 0 (car graphPosition))))
        (if (eq? (car graphPosition) 0) (set! input (list  1 (cadr graphPosition))))
       input)))
        

    ;; Standard filter procedure, as defined in SRFI1

    (define filter

      (lambda (predicate? lst)

	(apply append (map (lambda (x) (if (predicate? x) (list x) '())) lst))))

    

    ;; Does any element of list satisify predicate?

    (define any?

      (lambda (predicate? lst)

	(and (not (null? lst)) (or (predicate? (car lst)) (any? predicate? (cdr lst))))))

    

    ;; Build a list containing n instances of x

    (define repeat

      (lambda (x n)

	(if (= n 0) '()	(cons (tree-copy x) (repeat x (1- n))))))

    

    ;; Evaluates thunk n times.

    (define dotimes

      (lambda (thunk n)

	(for-each (lambda (i) (thunk)) (iota n))))

    

    ;; First n elements of lst

    (define take

      (lambda (lst n)

	(if (= n 0) '() (cons (car lst) (take (cdr lst) (1- n))))))

    

    ;; Haskell style zipWith

    ;; e.g. (zipWith + (1 2 3) (1 5 9)) => (2 7 12)

    ;; lesser scheme implementations do not like (lambda (x . y) ...)

    (define (zipWith proc . lsts)

      (let ((min-len (apply min (map length lsts))))

	(apply map (cons proc (map (lambda (l) (take l min-len)) lsts)))))

    

    ;; Counts instance of x in lst with eq?

    (define count

      (lambda (x lst)

	(length (filter (lambda (el) (eq? el x)) lst))))



    ;; Common Lisp style iota

    ;; (iota n)   => (0 1 2 ... n)

    ;; (iota n m) => (n n+1 n+2 ... m)

    (define (iota . args)

      (define iter

	(lambda (lower upper)

	  (cond ((= lower upper) '())

		(else (cons lower (iter (1+ lower) upper))))))

      (if (null? (cdr args))

	  (iter 0 (car args))

	  (iter (car args) (cadr args))))

    

    ;; Most schemes define this, very similar to 1+ 

    (define 1-

      (lambda (x)

	(- x 1)))



    ;; Haskell style concatMap, f should take an element and return a list, 

    ;; these lists are then merged into a single list.

    (define concat-map

      (lambda (f lst)

	(apply append (map f lst))))



    ;; Flattens an arbitarily nested list

    (define enumerate-tree

      (lambda (tree)

	(if (list? tree) (apply append (map enumerate-tree tree)) (list tree))))



    ;;; Helper procedures



    ;; Gets a list of positions in a given direction out from a given position. 

    ;; Second argument (i in [1..8]) defines direction as follows:

    ;; 8 1 2

    ;; 7 X 3

    ;; 6 5 4

    (define get-line-positions

      (lambda (position i)



	(define smart-zip

	  (lambda (lst1 lst2)

	    (cond ((not (list? lst1))

		   (zipWith make-position (repeat lst1 (length lst2)) lst2))

		  ((not (list? lst2))

		   (zipWith make-position lst1 (repeat lst2 (length lst1))))

		  (else

		   (zipWith make-position lst1 lst2)))))



	(let* ((row           (get-row position))

               (column        (get-column position))

	       (fetch-rows    (cond ((member i '(8 1 2)) (reverse (iota 0 row)))     

				    ((member i '(4 5 6)) (iota (1+ row) *NUM-ROWS*))

				    (else row)))

	       (fetch-columns (cond ((member i '(6 7 8)) (reverse (iota 0 column)))        

				    ((member i '(2 3 4)) (iota (1+ column) *NUM-COLUMNS*)) 

				    (else column))))

	  

	  (smart-zip fetch-rows fetch-columns))))



    ;; Get a list of all possible positions, open or otherwise

    (define enumerate-positions

      (lambda ()

	(concat-map 

	 (lambda (row)

	   (map (lambda (column) (make-position row column)) (iota *NUM-ROWS*)))

	 (iota *NUM-COLUMNS*))))
	
;;Get a list of all playable (unblocked) moves on the board
;; NOT IN INPUT FORM i.e. (1 n) or ( 0 n)
(define get-valid-positions
  (lambda (board)
    (let ((rows (iota *NUM-ROWS*)) (cols (iota *NUM-COLUMNS*)) (valid-moves '()))
      (map (lambda (x) 
                  (if (eq? (get-position (list x 0) board) *EMPTY-SYMBOL*)
                        (set! valid-moves (append valid-moves (list (list x 0)))))) rows)
      (map (lambda (y) 
                  (if (eq? (get-position (list 0 y) board) *EMPTY-SYMBOL*)
                        (set! valid-moves (append valid-moves (list (list 0 y)))))) cols)
      valid-moves)))

(define get-random-valid-position

      (lambda (board)
       (let ((open-positions (get-valid-positions board)))

	  (list-ref open-positions (random (length open-positions))))))


    
(define can-move?
  (lambda (position board)
    (let ((input (input->position position)) (moves (get-valid-positions board)) (isValid #f))
      (for-each (lambda (pos)
                  (if (equal? input pos) (set! isValid #t))) moves) isValid)))
    

    ;; Can player move on given board

(define has-move?
  (lambda (player board)

    (if (eq? (get-valid-positions board) '()) #f #t)))



    ;; Gets the next player for board given current-player

    ;; Returns 'PLAYER-1-SYMBOL, 'PLAYER-2-SYMBOL, or 'game-over

    (define next-player

      (lambda (current-player board)

	(let ((other (other-player current-player)))

	  (cond ((check-win *PLAYER-1-SYMBOL* board) 'game-over)
	        ((check-win *PLAYER-2-SYMBOL* board) 'game-over)
	        ((has-move? other board) other)

		 ((has-move? current-player board) current-player)

		     (else 'game-over)))))

    

    ;; Returns 'PLAYER-1-SYMBOL, 'PLAYER-2-SYMBOL, or 'tie

    (define get-winner

      (lambda (board)

	    (cond ((check-win *PLAYER-1-SYMBOL* board) *PLAYER-1-SYMBOL*)
	          ((check-win *PLAYER-2-SYMBOL* board) *PLAYER-2-SYMBOL*)

	           (else 'tie))))
;;check for 4 in a row
(define check-win
 (lambda (symbol board)
   (let ((rows (iota *NUM-ROWS*)) (cols (iota *NUM-COLUMNS*)) 
         (mdiag (iota (length *MAIN-DIAG*))) (cdiag (iota (length *COUNTER-DIAG*))) (win #f))
         (map (lambda (pos)
                 (if (> (sym-count symbol (select-diag pos board)) 3)
                     (set! win #t))) mdiag)
         (map (lambda (pos)
                 (if (> (sym-count symbol (select-counter-diag pos board)) 3)
                     (set! win #t))) cdiag)
         (map (lambda (pos)
                 (if (> (sym-count symbol (select-row pos board)) 3)
                     (set! win #t))) rows)
         (map (lambda (pos)
                 (if (> (sym-count symbol (select-column pos board)) 3)
                     (set! win #t))) cols)
         win)))

    

    ;; Gets a move from the human and doesn't give up

    (define get-human-move

      (lambda (player board board-string)

	(define handle-invalid

	  (lambda (invalid-string) 

	    (newline) (display board-string)

	    (newline) (display invalid-string)

	    (newline) (display (prompt-string player))

	    (newline) (get-human-move player board board-string)))

	

	(define get-position

	  (lambda ()

	    (let ((row '()) (column '()))

	      (display *ROW-PROMPT*) (flush-output) (set! row (read))

	      (display *COLUMN-PROMPT*) (flush-output) (set! column (read))

	      (make-position row column))))

	

	     (let ((position (get-position)))

	  (cond ((not (valid-position? position))

		                 (handle-invalid *INVALID-MOVE-FORM-STRING*))

		 ((not (can-move? position board))

		                 (handle-invalid *CANNOT-MOVE-STRING*))

		(else position)))))



    ;; Converts a board to a string, should use with-output-to-string

    ;; instead of building big tree and flattening it.

    (define board->string

      (lambda (board)

	(define symbol->string

	  (lambda (symbol)

	    (cond ((eq? symbol *PLAYER-1-SYMBOL*) " X ")

		  ((eq? symbol *PLAYER-2-SYMBOL*) " O ")

		  ((eq? symbol *EMPTY-SYMBOL*)    "   ")

		  ((eq? symbol *BLOCKED-SYMBOL*)  "+++"))))

	

	(define row->string-tree

	  (lambda (row-num)

	    (list (number->string row-num) 

		  "|"

		  (map (lambda (column-num) 

			 (list (symbol->string (get-position (make-position row-num column-num) board)) "|")) 

		       (iota *NUM-COLUMNS*))

		  "\n")))

	

	(define header-row

	  (list " |" (map (lambda (i) (list " " (number->string i) " |")) (iota *NUM-COLUMNS*)) "\n"))



	(define hr

	  (list "-|" (repeat "---|" *NUM-COLUMNS*) "\n"))

	

	(apply string-append

	       (enumerate-tree

		(list header-row 

		      hr 

		      (map (lambda (row-num) (list (row->string-tree row-num) hr)) (iota *NUM-ROWS*)))))))



    ;; Convert file string to player-procedure

    (define file->player 

      (lambda (file)

	(cond ((equal? file 'human) 'human)

	      (else

	       (set! player-procedure #f)

	       (load file)

	       (if player-procedure player-procedure (error "Player procedure not defined"))))))

    

    (let* ((player1-procedure (file->player player1-file))

	   (player2-procedure (file->player player2-file))

	   (current-player *PLAYER-1-SYMBOL*)

	   (board (make-new-board)))

      

      ;; Gets a position from human or player procedure

      (define get-a-position

	(lambda (board-string)

	  (let ((player-procedure (if (eq? current-player *PLAYER-1-SYMBOL*) player1-procedure player2-procedure)))

	    (if (eq? player-procedure 'human)

		(get-human-move current-player board board-string)

		(player-procedure current-player (tree-copy board))))))



      ;; Adjusts board to reflect player moving to position

      (define make-move!

	(lambda (position player board)

	  (define move! (lambda (position) (set-position! position player board)))

	  (move! position)))





      (define do-delay

	(lambda () 

	  (if (not (or (eq? player1-file 'human) (eq? player2-file 'human)))

	      (begin

		(sleep-current-thread *SLEEP-MILLISECONDS*)

		(if *STALL* (begin (display *WAIT-PROMPT*) (flush-output) (read-line)))

		(newline)))))



      ;; Main program loop

      (define loop

	(lambda ()

	  (let* ((board-string (board->string board))

		 (position '()))

	    (display board-string) (newline)

	    (display (prompt-string current-player)) (newline)

	    (set! position (get-a-position board-string))

	     
            (cond

	     ((and (valid-position? position)

		   (can-move? position board))

	      (make-move! position current-player board)	

	      (set! current-player (next-player current-player board))

	      (if (eq? current-player 'game-over)

		  (let ((winner (get-winner board)))

		    (display (board->string board)) (newline)

		    (display (winner-string winner)) (newline)

		    winner)

		  (begin (sleep-current-thread *SLEEP-MILLISECONDS*) 

			 (do-delay)

			 (loop))))

	     (else (display *GAME-OVER-INVALID-MOVE*) (newline)

		   (display (winner-string (other-player current-player))) (newline)

		   (other-player current-player))))))

      (loop))))
```

Here is my code for my player:
```


(define player-procedure

  (let () 


    (define counter 1)
    (define counter2 0)

    (define *NUM-ROWS* 6)

    (define *NUM-COLUMNS* 7)

	

    (define *PLAYER-1-SYMBOL* 'x)

    (define *PLAYER-2-SYMBOL* 'o)

    (define *EMPTY-SYMBOL* '())

    

    (define *INVALID-MOVE-FORM-STRING* "Invalid position specified.")

    (define *CANNOT-MOVE-STRING* "Cannot move to specified position.")

    (define *ROW-PROMPT*    "Select side (0-left, 1-top): ")

    (define *COLUMN-PROMPT* "Select row: ")



    (define *PLAYER-1-PROMPT* "Player 1's Turn (X)")

    (define *PLAYER-2-PROMPT* "Player 2's Turn (O)")

    

    (define *GAME-OVER-INVALID-MOVE*    "Invalid move returned by player procedure.")

    (define *GAME-OVER-TIE-STRING*      "Game over: Game ends in tie.")

    (define *GAME-OVER-PLAYER-1-STRING* "Game over: Player 1 (X) wins.")

    (define *GAME-OVER-PLAYER-2-STRING* "Game over: Player 2 (0) wins.")



    (define *SLEEP-MILLISECONDS* 0)

    (define *STALL* #t)



    (define *WAIT-PROMPT*    "Hit enter to continue:")


	(define *ALL-MOVES* '((list 0 0) (list 0 1) (list 0 2) (list 0 3) (list 0 4) (list 0 5) (list 0 6)
                          (list 1 0) (list 2 0) (list 3 0) (list 4 0) (list 5 0)))
    (define *MAIN-DIAG* (list (list 2 0) (list 1 0) (list 0 0) (list 0 1) (list 0 2) (list 0 3)))
	(define *COUNTER-DIAG* (list (list 3 0) (list 4 0) (list 5 0) (list 5 1) (list 5 2) (list 5 3)))





    (define make-position 

      (lambda (row column)

	(list row column)))

      

    ;; Row accessor

    (define get-row 

      (lambda (move)

	(car move)))

    

    ;; Column accessor

    (define get-column 

      (lambda (move)

	(cadr move)))

    

    ;; Does the given move have a valid form

    (define valid-position?

      (lambda (inputPosition)
       (let ((position (input->position inputposition)))

	(let ((integer<=? (lambda (x n) (and (integer? x) (< -1 x n)))))

	  (and (list? position) (= 2 (length position))

	       (integer<=? (get-row position) *NUM-ROWS*)

	       (integer<=? (get-column position) *NUM-COLUMNS*))))))


    

    ;;; Board abstraction



    ;; Sets a position on the board

   (define set-position!

  (lambda (position value board)

	(let ((pos (input->position position)))
	  (if (eq? (car position) 0)
           (set-car! (list-tail (list-ref board (cadr position)) 
               (+ (get-deepest-pos (positions->sym-lst (get-line-positions pos 3) board))1)) value)

	  (if (eq? (car position) 1) 
	       (set-car! (list-tail (list-ref board 
	          (+(get-deepest-pos (positions->sym-lst (get-line-positions pos 5) board))1)) (cadr position)) value))))))



    ;; Gets the value of the board at a given position

    (define get-position

     (lambda (position board)

	   (list-ref (list-ref board (get-row position)) (get-column position))))



    

    ;; Builds new board

    (define make-new-board

      (lambda ()

	(let ((board (repeat (repeat *EMPTY-SYMBOL* *NUM-COLUMNS*) *NUM-ROWS*)))

	  board)))

    

    ;;; Utilitiy procedures
    
    ;; converts a list of positions into their respective symbols
(define positions->sym-lst
  (lambda (position-lst board)
    (let ((sym-list '()))
      (for-each (lambda (position) 
                 (set! sym-list (append sym-list (list (get-position position board))))) position-lst)
                  sym-list)))

    
    ;;returns a copy of the row
(define select-row
  (lambda (row board)
    (positions->sym-lst (cons (list row 0) (get-line-positions (list row 0) 3)) board)))

(define select-column
  (lambda (col board)
    (positions->sym-lst (cons (list 0 col) (get-line-positions (list 0 col) 5)) board)))

(define select-diag
  (lambda (diag board)
    (positions->sym-lst (cons (list-ref *MAIN-DIAG* diag) (get-line-positions (list-ref *MAIN-DIAG* diag) 4)) board)))
    
(define select-counter-diag
  (lambda (diag board)
    (positions->sym-lst (cons (list-ref *COUNTER-DIAG* diag) (get-line-positions (list-ref *COUNTER-DIAG* diag) 2)) board)))

;;returns the "deepest *EMPTY-SYMBOL* in the lst, -1 if none
(define get-deepest-pos
  (lambda (lst)
     (let ((count -1) (stillEmptySym #t))
       (for-each (lambda (element)
                   (if stillEmptySym
                         (if (eq? element *EMPTY-SYMBOL*) (set! count (+ count 1))
                                                    (set! stillEmptySym #f))))
       lst)
       count)))

(define sym-count
  (lambda (symbol lst)
    (let ((runSum 0) (sumMax 0))
      (for-each (lambda (el) 
                      (if (eq? el symbol)
                          (set! runSum (+ runSum 1))
                          (if (> runSum sumMax) (begin (set! sumMax runSum)
                                                       (set! runSum 0))
                              (set! runSum 0)))) lst)
      (if (> runSum sumMax) runSum sumMax))))
    
  ;;converts input to the board coordinate equiv
  (define input->position
    (lambda (inputPosition)
     (let ((position '()))
       (if (eq? (car inputPosition) 0) (set! position (list (cadr inputPosition) 0)))
       (if (eq? (car inputPosition) 1) (set! position (list 0 (cadr inputPosition))))
       position)))
    

    ;; Standard filter procedure, as defined in SRFI1

    (define filter

      (lambda (predicate? lst)

	(apply append (map (lambda (x) (if (predicate? x) (list x) '())) lst))))

    

    ;; Does any element of list satisify predicate?

    (define any?

      (lambda (predicate? lst)

	(and (not (null? lst)) (or (predicate? (car lst)) (any? predicate? (cdr lst))))))

    

    ;; Build a list containing n instances of x

    (define repeat

      (lambda (x n)

	(if (= n 0) '()	(cons (tree-copy x) (repeat x (1- n))))))

    

    ;; Evaluates thunk n times.

    (define dotimes

      (lambda (thunk n)

	(for-each (lambda (i) (thunk)) (iota n))))

    

    ;; First n elements of lst

    (define take

      (lambda (lst n)

	(if (= n 0) '() (cons (car lst) (take (cdr lst) (1- n))))))

    

    ;; Haskell style zipWith

    ;; e.g. (zipWith + (1 2 3) (1 5 9)) => (2 7 12)

    ;; lesser scheme implementations do not like (lambda (x . y) ...)

    (define (zipWith proc . lsts)

      (let ((min-len (apply min (map length lsts))))

	(apply map (cons proc (map (lambda (l) (take l min-len)) lsts)))))

    

    ;; Counts instance of x in lst with eq?

    (define count

      (lambda (x lst)

	(length (filter (lambda (el) (eq? el x)) lst))))



    ;; Common Lisp style iota

    ;; (iota n)   => (0 1 2 ... n)

    ;; (iota n m) => (n n+1 n+2 ... m)

    (define (iota . args)

      (define iter

	(lambda (lower upper)

	  (cond ((= lower upper) '())

		(else (cons lower (iter (1+ lower) upper))))))

      (if (null? (cdr args))

	  (iter 0 (car args))

	  (iter (car args) (cadr args))))

    

    ;; Most schemes define this, very similar to 1+ 

    (define 1-

      (lambda (x)

	(- x 1)))



    ;; Haskell style concatMap, f should take an element and return a list, 

    ;; these lists are then merged into a single list.

    (define concat-map

      (lambda (f lst)

	(apply append (map f lst))))



    ;; Flattens an arbitarily nested list

    (define enumerate-tree

      (lambda (tree)

	(if (list? tree) (apply append (map enumerate-tree tree)) (list tree))))



    ;;; Helper procedures



    ;; Gets a list of positions in a given direction out from a given position. 

    ;; Second argument (i in [1..8]) defines direction as follows:

    ;; 8 1 2

    ;; 7 X 3

    ;; 6 5 4

    (define get-line-positions

      (lambda (position i)



	(define smart-zip

	  (lambda (lst1 lst2)

	    (cond ((not (list? lst1))

		   (zipWith make-position (repeat lst1 (length lst2)) lst2))

		  ((not (list? lst2))

		   (zipWith make-position lst1 (repeat lst2 (length lst1))))

		  (else

		   (zipWith make-position lst1 lst2)))))



	(let* ((row           (get-row position))

               (column        (get-column position))

	       (fetch-rows    (cond ((member i '(8 1 2)) (reverse (iota 0 row)))     

				    ((member i '(4 5 6)) (iota (1+ row) *NUM-ROWS*))

				    (else row)))

	       (fetch-columns (cond ((member i '(6 7 8)) (reverse (iota 0 column)))        

				    ((member i '(2 3 4)) (iota (1+ column) *NUM-COLUMNS*)) 

				    (else column))))

	  

	  (smart-zip fetch-rows fetch-columns))))
	
;;Get a list of all playable (unblocked) moves on the board
(define get-valid-positions
  (lambda (board)
    (let ((rows (iota *NUM-ROWS*)) (cols (iota *NUM-COLUMNS*)) (valid-moves '()))
      (map (lambda (x) 
                  (if (eq? (get-position (list x 0) board) *EMPTY-SYMBOL*)
                        (set! valid-moves (append valid-moves (list (list x 0)))))) rows)
      (map (lambda (y) 
                  (if (eq? (get-position (list 0 y) board) *EMPTY-SYMBOL*)
                        (set! valid-moves (append valid-moves (list (list 0 y)))))) cols)
      valid-moves)))

;;Get a list of all opponents moves on the board
(define get-opponents-positions
  (lambda (board)
    (let ((rows (iota *NUM-ROWS*)) (cols (iota *NUM-COLUMNS*)) (opponents-moves '()))
      (if (= (/ counter 2) 0)
      ((map (lambda (x) 
                  (if (eq? (get-position (list x 0) board) *PLAYER-1-SYMBOL*)
                        (set! opponents-moves (append opponents-moves (list (list x 0)))))) rows)
      (map (lambda (y) 
                  (if (eq? (get-position (list 0 y) board) *PLAYER-1-SYMBOL*)
                        (set! opponents-moves (append opponents-moves (list (list 0 y)))))) cols))
      ((map (lambda (x) 
                  (if (eq? (get-position (list x 0) board) *PLAYER-2-SYMBOL*)
                        (set! opponents-moves (append opponents-moves (list (list x 0)))))) rows)
      (map (lambda (y) 
                  (if (eq? (get-position (list 0 y) board) *PLAYER-2-SYMBOL*)
                        (set! opponents-moves (append opponents-moves (list (list 0 y)))))) cols)))
      opponents-moves
      (set! counter (+ counter 1)))))

(define position->input
    (lambda (graphPosition)
      (let ((input '()))
        (if (eq? (cadr graphPosition) 0) (set! input (list 0 (car graphPosition))))
        (if (eq? (car graphPosition) 0) (set! input (list  1 (cadr graphPosition))))
       input)))

[B]
(define (valid? x y)
    (if (null? y)
        #f
        (if (and (= (caar x) (caadr y)) (= (cadar x) (car (cdadr y))))
         (#t (set! counter2 (+ counter2 1)))
            (valid? x (cdr y)))))

(define get-player-position

      (lambda (board)
       (let ((open-positions (get-valid-positions board)))

        (let ((opp-moves (get-opponents-positions board)))   
          (define (blockv opp-moves position)
           (if (null? opp-moves) 'false
               (if (= (caar opp-moves) (caadr opp-moves))
                   (if (and (< (cadar opp-moves) (car (cdadr opp-moves))) (> (cadar opp-moves) (- (car (cdadr opp-moves)) 2)) (valid? (car opp-moves) open-positions)) counter2
                     (if (and (> (cadar opp-moves) (car (cdadr opp-moves))) (< (cadar opp-moves) (- (car (cdadr opp-moves)) 2)) (valid? (car opp-moves) open-positions)) counter2 
                (blockv (cdr opp-moves) position))))))
          (define (blockh opp-moves position)
           (if (null? opp-moves) 'false
               (if (= (cadar opp-moves) (car (cdadr opp-moves)))
                   (if (and (< (caar opp-moves) (caadr opp-moves)) (> (caar opp-moves) (- (caadr opp-moves)) 2) (valid? (car opp-moves) open-positions)) counter2
                     (if (and (> (caar opp-moves) (caadr opp-moves)) (< (caar opp-moves) (- (caadr opp-moves)) 2) (valid? (car opp-moves) open-positions)) counter2 
                (blockh (cdr opp-moves) position))))))

            (cond ((and (eq? (blockh opp-moves 0) 'false) (eq? (blockv opp-moves 0) 'false)) (list-ref open-positions 0))
                  ((eq? (blockh opp-moves 0) 'false) (list-ref open-positions counter2))
                  ((eq? (blockv opp-moves 0) 'false) (list-ref open-positions counter2))
                  (else (list-ref open-positions 0)))))))
    



    (define (get-move player board)

      (position->input (get-player-position board)))


    get-move))
[/B]

```

Highlighted is the code I have changed.  The code will compile, but when I try to play the game, I get the error:
```
;The object (#!unspecific #!unspecific #!unspecific #!unspecific #!unspecific #!unspecific) is not applicable.
```

Was wondering if anyone could help me figure this out.

---

