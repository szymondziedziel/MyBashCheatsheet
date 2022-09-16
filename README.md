```
> cat data.csv # Simply prints file content
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> alias tac='tail -r' # I believe tac comes from brew install coreutils, but can be made from tail program/ command
---
> tac data.csv # tac is for print file content but in reverse way, X-mirrored
ROW_5_COL_1,ROW_5_COL_2,4
ROW_4_COL_1,ROW_4_COL_2,3
ROW_3_COL_1,ROW_3_COL_2,2
ROW_2_COL_1,ROW_2_COL_2,1
ROW_1_COL_1,ROW_1_COL_2,0
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
---
> cat -n data.csv # Add -n flag to cat to number lines automatically for you
     1	COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
     2	ROW_1_COL_1,ROW_1_COL_2,0
     3	ROW_2_COL_1,ROW_2_COL_2,1
     4	ROW_3_COL_1,ROW_3_COL_2,2
     5	ROW_4_COL_1,ROW_4_COL_2,3
     6	ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | rev # Print file content in reverse way, Y-mirrored
REBMUN_REDAEH_NMULOC,B_REDAEH_NMULOC,A_REDAEH_NMULOC
0,2_LOC_1_WOR,1_LOC_1_WOR
1,2_LOC_2_WOR,1_LOC_2_WOR
2,2_LOC_3_WOR,1_LOC_3_WOR
3,2_LOC_4_WOR,1_LOC_4_WOR
4,2_LOC_5_WOR,1_LOC_5_WOR
---
> cat data.csv | cut -d',' -f1 # Cut columns by delimeter, here by comma, take 1 column, bash starts counting from 1 for cut and sed
COLUMN_HEADER_A
ROW_1_COL_1
ROW_2_COL_1
ROW_3_COL_1
ROW_4_COL_1
ROW_5_COL_1
---
> cat data.csv | cut -d',' -f1,2 # Cut columns 1 and 2
COLUMN_HEADER_A,COLUMN_HEADER_B
ROW_1_COL_1,ROW_1_COL_2
ROW_2_COL_1,ROW_2_COL_2
ROW_3_COL_1,ROW_3_COL_2
ROW_4_COL_1,ROW_4_COL_2
ROW_5_COL_1,ROW_5_COL_2
---
> cat data.csv | cut -d',' -f1-3 # Cut columns from 1 to 3, i. e. 1, 2 and 3. Unfortunately cannot change order :(, but maybe this command allows it?
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | sed -n '1p' # Print first line. Use -n flag to print only selected lines
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
---
> cat data.csv | sed -n '2,$p' # Print from line 2 to end thanks to $ character
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | sed -n '2,4p' # Print from line 2 to 4, yes ROW_1 is seconds line as HEADERS goes as first
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
---
> cat data.csv | sed '1d' # Delete first line. Skip -n flag here, HEADERS removed as they are first line
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | sed '$d' #  Delete last line, yes $ character means last line in sed
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
---
> cat data.csv | sed '2,4d' # Delete lines 2 to 4
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | grep 'ROW_4' # Simply selects all lines that contains ROW_4
ROW_4_COL_1,ROW_4_COL_2,3
---
> cat data.csv | grep 'COL_2' # Simply selects all lines that contains COL_2
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | grep -oE '[^,]+' # Split all lines in file by character, comma in this case
COLUMN_HEADER_A
COLUMN_HEADER_B
COLUMN_HEADER_NUMBER
ROW_1_COL_1
ROW_1_COL_2
0
ROW_2_COL_1
ROW_2_COL_2
1
ROW_3_COL_1
ROW_3_COL_2
2
ROW_4_COL_1
ROW_4_COL_2
3
ROW_5_COL_1
ROW_5_COL_2
4
---
> cat data.csv | grep -v 'HEADER' # Selects all-except lines containing HEADER
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> cat data.csv | grep -oE '.{7}' # Chunk every 7 character from file, threat whole content as 'single line'
COLUMN_
HEADER_
A,COLUM
N_HEADE
R_B,COL
UMN_HEA
DER_NUM
ROW_1_C
OL_1,RO
W_1_COL
ROW_2_C
OL_1,RO
W_2_COL
ROW_3_C
OL_1,RO
W_3_COL
ROW_4_C
OL_1,RO
W_4_COL
ROW_5_C
OL_1,RO
W_5_COL
---
> cat data.csv | grep -oE '^.{7}' # When match beginning of the line with ^ character then takes 7 characters for each line
COLUMN_
ROW_1_C
ROW_2_C
ROW_3_C
ROW_4_C
ROW_5_C
---
> cat data.csv | xargs # Simply wraps all lines into one separates with spaces. xargs is more powerfull than that. Useful for 'for' loops
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER ROW_1_COL_1,ROW_1_COL_2,0 ROW_2_COL_1,ROW_2_COL_2,1 ROW_3_COL_1,ROW_3_COL_2,2 ROW_4_COL_1,ROW_4_COL_2,3 ROW_5_COL_1,ROW_5_COL_2,4
---
> pbpaste # CMD+V in terminal
---
> echo "test" | pbcopy # Puts test in CMD+V, ready to paste
---
> pbpaste # See, we copied test, it pastes test for us
test
---
> open http://google.com # Opens entry with default program
---
# tail # to simulate tac as we saw at the beginning
> tail -n 3 data.csv # Also tail to select lines from end of file content. Put -n flag and follow it with number of lines
ROW_3_COL_1,ROW_3_COL_2,2
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
---
> head -n 3 data.csv # head to select lines from beginning of file content. Put -n flag and follow it with number of lines
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_1_COL_1,ROW_1_COL_2,0
ROW_2_COL_1,ROW_2_COL_2,1
---
> cat data.csv | wc -c # Count characters
     183
---
> cat data.csv | wc -w # Count words
       6
---
> cat data.csv | wc -l # Count lines
       6
---
> cat data.csv | sed 's/,/ /g' | wc -w # Let's replace all commas with spaces, it gives us more words :)
      18
---
> seq 0 10 # Simply sequence from 0 to 10 inclusive
0
1
2
3
4
5
6
7
8
9
10
---
> seq 0 2 10 # Simply sequence from 0 to 10 inclusive, but with step 2
0
2
4
6
8
10
---
> for number in $(seq 0 10); do; echo "NEXT_NUMBER=[$number]"; done # seq is useful in for loops
NEXT_NUMBER=[0]
NEXT_NUMBER=[1]
NEXT_NUMBER=[2]
NEXT_NUMBER=[3]
NEXT_NUMBER=[4]
NEXT_NUMBER=[5]
NEXT_NUMBER=[6]
NEXT_NUMBER=[7]
NEXT_NUMBER=[8]
NEXT_NUMBER=[9]
NEXT_NUMBER=[10]
---
> brew install coreutils # for tac and shuf
---
> shuf data.csv # Reads lines from file, shuffles them and prints
ROW_1_COL_1,ROW_1_COL_2,0
ROW_4_COL_1,ROW_4_COL_2,3
ROW_5_COL_1,ROW_5_COL_2,4
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
ROW_2_COL_1,ROW_2_COL_2,1
ROW_3_COL_1,ROW_3_COL_2,2
---
> shuf data.csv | sed -n '1p' # Shuffles lines in file and takes first. Thanks to this we can get different results
ROW_3_COL_1,ROW_3_COL_2,2
---
> shuf data.csv | sed -n '1p'
ROW_1_COL_1,ROW_1_COL_2,0
---
> shuf data.csv | sed -n '1p'
COLUMN_HEADER_A,COLUMN_HEADER_B,COLUMN_HEADER_NUMBER
---
> shuf data.csv | sed -n '1p'
ROW_1_COL_1,ROW_1_COL_2,0
---
> echo $RANDOM # Random int
9150
---
> echo $RANDOM
7004
---
> echo $RANDOM
23123
---
> echo $RANDOM
2950
---
> echo $RANDOM
5839
---
> echo $RANDOM
6789
---
> echo $RANDOM
9247
---
> tree . # List files as tree from selected directory recursively.
.
├── README.md
└── data.csv

0 directories, 2 files
```

Some real life examples:

- Sum all values from data.csv file from HEADER_NUMBER column
- Take first 7 characters of current git hash commit
- Get files extensions for files e. g. from this repo root
- Extract URL query params
- Take only devices serials numbers from adb-devices.txt

Scroll a bit down to see solutions
```
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
```
- Sum all values from data.csv file from HEADER_NUMBER column

`echo $(($(cat data.csv| sed '1d' | cut -d',' -f3 | xargs | sed 's/ / + /g')))`

- Take first 7 characters of current git hash commit

`git --no-pager log | sed -n '1p' | cut -d' ' -f2 | grep -oE '^.{7}'`

- Get files extensions for files e. g. from this repo root

`ls | rev | cut -d'.' -f1 | rev`

- Extract URL query params

`echo 'https://example.com/path/to/page?name=ferret&color=purple' | grep -oE '[^?&]+' | sed -n '2,$p'`

- Take only devices serials numbers from adb-devices.txt

`cat adb-devices.txt | sed '1d' | cut -d' ' -f1`
