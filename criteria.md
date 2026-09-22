# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
I picked 4 of 5 because question 5 (where to stay near Givens Mill) is likely to be the hardest. Every town guide has a "Where to stay" section with similar wording, so retrieval might return another town's section. The correct answer is also "Brightwater," another town's name, which makes a mix-up more likely.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
I expect all 5 because every retrieved chunk is labeled with its source file, and the grounding prompt tells the model to cite the file. In my first test answer, it cited a file after every fact. The only way this fails is if the model ignores that instruction. 

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

**Why this target:**
<!-- What did your distances look like when you set the cutoff in Milestone 4?
     Was there a clean gap, or did the two groups overlap? -->
Most of the off-topic questions share nothing with travel guides, so their distances should be far from the cutoff. The diesel engine question overlaps a little with the transport sections, so I'm leaving room for one to slip through.

---

## 4. Something about your chunks

Across all chunks, every chunk covers exactly one section of one guide (at most one "##" heading), and every chunk names the town or guide it comes from.


**Why this target:**
My questions each ask about one topic in one town, and the starter's chunker cut through section headings. Some sections also never name their own town (Givens Mill's "Where to stay" only mentions Brightwater), so the town name has to be in the chunk. 


---

## 5. Your choice

For at least 4 of my 5 test questions, the answer cites the guide for the town the question
asks about.

**Why this target:**
Criterion 2 only checks that a source is named, not that it's the right one. I picked 4 of 5 because question 5's answer is "Brightwater," so the model may cite Brightwater's guide instead of Givens Mill's


---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
