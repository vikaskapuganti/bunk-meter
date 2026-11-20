# Bunk Meter

Know exactly how many classes you can bunk and still stay above 75%.

Bunk Meter is a free attendance tracker for college students. Add your subjects, tap **Attended** or **Bunked** after every class, and it tells you, for each subject and overall:

- your attendance right now
- how many more classes you can safely bunk
- or, if you're below the line, how many classes in a row you need to attend

**Use it here:** https://vikaskapuganti.github.io/bunk-meter/

Built by [Vikas Kapuganti](https://instagram.com/vikas_senior), as Day 1 of the *15 Problems. 15 AI Solutions.* challenge.

---

## How to use it

1. **Pick how many subjects you have.** Labs count too, if your college takes attendance for them.
2. **Name your subjects** (optional). For example DBMS, OS, CN, OS Lab.
3. **Already have attendance?** Turn on "I already know my attendance" and enter classes attended and classes held so far for each subject. Otherwise everything starts at zero.
   - **Know how many classes your semester will have?** Add the total expected this semester (optional). Bunk Meter then tells you how many of the remaining classes you can bunk, or whether 75% is still reachable.
4. **Choose your college's rule.** 75% is the default. You can pick 65%, 70% or 80%.
5. **After every class**, tap **Attended** or **Bunked** on that subject. Tapped the wrong one? Tap **Undo**.
6. **Tap Can I bunk?** on any subject for a straight Yes, Risky or No, plus a planner: "if 10 more classes happen and I bunk 2, where will I be?"
7. **When your college shares real numbers**, tap **Edit** on the subject and type them in. The count corrects itself.

Tip: open Settings and tap **Add to home screen**. It then opens like an app and works without internet.

## Privacy

- No login, no account, no ads.
- Your data is saved only on your own phone, in your browser. Nothing is sent anywhere.
- Clearing your browser data deletes it. Add Bunk Meter to your home screen, and take a screenshot of your numbers now and then (or use **Settings > Back up my data**).

Your college's attendance records are final. Bunk Meter is a guide to help you plan.

## How the numbers are worked out

With `A` classes attended out of `T` total and a target of `P` (for example 0.75):

- **Classes you can bunk** = the largest `x` where `A / (T + x)` is still at least `P`, which is `floor(A / P - T)`
- **Classes you need to attend** = the smallest `y` where `(A + y) / (T + y)` reaches `P`, which is `ceil((P*T - A) / (1 - P))`. Every class you attend also adds to the total, which is why this number grows fast.
- **With an expected total `E`:** classes left `R = E - T`, classes you must attend `N = ceil(P*E) - A`. You can bunk `R - N` of them. If `N` is more than `R`, the target can't be reached this semester.

Percentages are rounded down, never up, so 74.96% shows as 74.9%, not 75%.

## Host your own copy (free)

Anyone can copy Bunk Meter and run it on their own GitHub. It's plain HTML, with no build step and no server.

**Option 1: Fork it (easiest)**
1. Sign in to GitHub and open this repository.
2. Click **Fork**, then **Create fork**.
3. In your fork, go to **Settings > Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then **Save**.
5. Wait a minute. Your copy is live at `https://YOUR-USERNAME.github.io/bunk-meter/`.

**Option 2: Upload the files**
1. Download this repository as a ZIP (**Code > Download ZIP**) and unzip it.
2. On GitHub, create a new public repository, for example `bunk-meter`.
3. Click **Add file > Upload files** and drag in everything from the unzipped folder, including the `icons` folder.
4. Commit, then turn on Pages as in step 3 to 5 above.

**Run it on your laptop:** just open `index.html` in a browser. (Offline mode only works once it's hosted on https.)

**Changing it:** everything is in `index.html`. If you edit any file, change `VERSION` at the top of `sw.js` (for example to `bunkmeter-v2`) so people get the new version instead of the saved old one.

## Files

| File | What it does |
|---|---|
| `index.html` | The whole app: layout, design and logic |
| `sw.js` | Lets the app work offline |
| `manifest.webmanifest` | Lets it be added to the home screen like an app |
| `icons/` | App icons |

## Can many people use it at once?

Yes. There's no server and no database. GitHub Pages just sends the same small page to everyone, and each student's data stays on their own phone. 100 users or 100,000 users work the same way.

## License

MIT. Free to use, copy and change. Please keep the credit line.
