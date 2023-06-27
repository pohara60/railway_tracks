# Puzzle Solver in Dart

Command line application to solve various puzzles, as printed in The Times.

```
dart run bin\puzzle.dart
```

## Train Tracks

The Train Tracks solver uses two ways to solve the puzzle:
1.  Logic - repeatedly applies logic identifying cells that have a track, finally determining the track that joins these cells.
2.  Backtracking - iteratively try all possible tracks.

Run example puzzle:
```
dart run bin\puzzle.dart train_tracks
 31225634
2........
2........
4╗..╔╝║..
6...╝....
4........
3........
4........
1....║...

Logic Solution
 OOOO╔╗OO
 OOOO║║OO
 ╗OO╔╝║OO
 ║O╔╝O╚═╗
 ╚═╝OOOO║
 OOOOO╔╗║
 OOOO╔╝╚╝
 OOOO║OOO

Backtrack Solution(s)
 OOOO╔╗OO
 OOOO║║OO
 ╗OO╔╝║OO
 ║O╔╝O╚═╗
 ╚═╝OOOO║
 OOOOO╔╗║
 OOOO╔╝╚╝
 OOOO║OOO

Solutions: 1, 524 iterations
```

Get help:
```
dart run bin\puzzle.dart -h train_tracks
Solve Train Tracks puzzle specified by <grid>, with <solution>.

The 1st argument <grid> is a list of N strings (rows) of length N (cells).
The 2nd argument specifies the <solution>, either as another full grid, or a list with rowCounts and colCounts.

The cells may be specified using the track characters "║═╚╔╗╝" or simply "x", with "." for unspecified, e.g.

train_tracks "........,........,╗..╔╝║..,...╝....,........,........,........,....║..." "34544331,13324644"
or
train_tracks "........,........,x..xxx..,...x....,........,........,........,....x..." "34544331,13324644"

Usage: puzzle train_tracks [arguments]
-h, --help    Print this usage information.

Run "puzzle help" to see global options.
```

## Futoshiki

The Futoshiki solver uses two ways to solve the puzzle:
1.  Logic - repeatedly applies logic regarding possible numbers in a cell, identifying cells that have only one possible value.
2.  Backtracking - iteratively try all possible legal combonations of numbers.

Run example puzzle:
```
dart run bin\puzzle.dart futoshiki   
. . . . 2
    >   <
. .<. . .
      <
. . . .<.
        <
3 . . . .
  >
. . . . .

updatePossible: R0C0=1345
updatePossible: R0C1=1345
updatePossible: R0C2=1345
updatePossible: R0C3=1345
updatePossible: R3C1=1245
updatePossible: R3C2=1245
updatePossible: R3C3=1245
updatePossible: R3C4=1245
updatePossible: R0C0=145
updatePossible: R1C0=1245
updatePossible: R2C0=1245
updatePossible: R4C0=1245
updatePossible: R1C4=1345
updatePossible: R2C4=1345
updatePossible: R3C4=145
updatePossible: R4C4=1345
updateConstraints: set max for R1C1=1234
updateConstraints: set min for R1C2=2345
updateConstraints: set max for R1C2=234
updateConstraints: set min for R0C2=345
updateConstraints: set min for R1C4=345
updateConstraints: set max for R1C3=1234
updateConstraints: set min for R2C3=2345
updateConstraints: set max for R2C3=234
updateConstraints: set min for R2C4=345
updateConstraints: set max for R2C4=34
updateConstraints: set min for R3C4=45
updateConstraints: set min for R3C1=245
updateConstraints: set max for R4C1=1234
updateConstraints: set max for R1C1=123
updateConstraints: set max for R1C3=123
updateConstraints: set max for R2C3=23
updateConstraints: set max for R1C3=12
Hidden Single: R4C4=1
updatePossible: R4C0=245
updatePossible: R4C1=234
updatePossible: R4C2=2345
updatePossible: R4C3=2345
updateConstraints: set min for R3C1=45
Naked Group: remove group 45 from R3C2=12
Naked Group: remove group 45 from R3C3=12
Naked Group: remove group 12 from R0C3=345
Naked Group: remove group 12 from R2C3=3
Naked Group: remove group 12 from R4C3=345
Naked Group: remove group 123 from R0C3=45
Naked Group: remove group 123 from R4C3=45
updateConstraints: set min for R2C4=4
updateConstraints: set min for R3C4=5
Hidden Single: R1C4=3
Naked Single: R2C3=3
Naked Single: R2C4=4
Hidden Single: R3C1=4
Naked Single: R3C4=5
updatePossible: R1C1=12
updatePossible: R1C2=24
updatePossible: R2C0=125
updatePossible: R2C1=125
updatePossible: R2C2=125
updatePossible: R0C1=135
updatePossible: R4C1=23
Hidden Single: R1C0=5
Hidden Single: R1C2=4
updatePossible: R0C0=14
updatePossible: R2C0=12
updatePossible: R4C0=24
updatePossible: R0C2=35
updatePossible: R4C2=235
updateConstraints: set min for R0C2=5
Hidden Single: R0C1=3
Naked Single: R0C2=5
Hidden Single: R2C1=5
Hidden Single: R4C2=3
Hidden Single: R4C3=5
updatePossible: R0C3=4
updatePossible: R2C2=12
updatePossible: R4C1=2
Hidden Single: R0C0=1
Naked Single: R0C3=4
Hidden Single: R1C1=1
Hidden Single: R1C3=2
Hidden Single: R3C3=1
Hidden Single: R4C0=4
Naked Single: R4C1=2
updatePossible: R3C2=2
updatePossible: R2C0=2
Naked Single: R2C0=2
Hidden Single: R2C2=1
Naked Single: R3C2=2
╔═══╤═══╤═══╤═══╤═══╗
║1  │  3│   │   │ 2 ║
║   │   │ 5 │4  │   ║
╟───┼───┼>>>┼───┼<<<╢
║   │1  <   │ 2 │  3║
║ 5 │   <4  │   │   ║
╟───┼───┼───┼<<<┼───╢
║ 2 │   │1  │  3<   ║
║   │ 5 │   │   <4  ║
╟───┼───┼───┼───┼<<<╢
║  3│   │ 2 │1  │   ║
║   │4  │   │   │ 5 ║
╟───┼>>>┼───┼───┼───╢
║   │ 2 │  3│   │1  ║
║4  │   │   │ 5 │   ║
╚═══╧═══╧═══╧═══╧═══╝

Logic Solution
1 3 5 4 2
    >   <
5 1<4 2 3
      <
2 5 1 3<4
        <
3 4 2 1 5
  >
4 2 3 5 1

Backtrack Solution(s)
1 3 5 4 2
    >   <
5 1<4 2 3
      <
2 5 1 3<4
        <
3 4 2 1 5
  >
4 2 3 5 1

Solutions: 1, 14564 iterations
```

Get help:
```
dart run bin\puzzle.dart -h futoshiki                                                
Solve Futoshiki puzzle specified by <grid>.

The argument <grid> is a list of 2N-1 strings (rows) of length 2N-1 (cells).
The odd rows have N optional grid entries in range 1 to N, separated by optional < or > signs to specify horizontal comparisons.
The even rows have optional < or > signs to specify column comparisons.

e.g. futoshiki ". . . . 2,    >   ^,. .<. . .,      <  ,. . . .<.,        <,3 . . . .,  >      ,. . . . ."

Usage: puzzle futoshiki [arguments]
-h, --help    Print this usage information.

Run "puzzle help" to see global options.
```

## To Do

Merge Tetonor repository.
Consider Codewords, KenKen, Kakuro.