# Assetto Corsa Lap Board

<img width="1280" height="340" alt="3639675974_preview_workflow" src="https://github.com/user-attachments/assets/52653a9f-51bf-4bed-940b-6aa35b7f0589" />

## What is this?
A public lap archive site for Assetto Corsa that reads straight from `personalbest.ini`. Just drive and break records, then use the included LapUpdater tool to push the changes. GitHub Actions will automatically process the data and update your site instantly

## Use it as a template
**Requirements:**
- git & github account
- (optional) github cli
- An `personalbest.ini` file from Assetto Corsa. You can find it in `user/Documents/Assetto Corsa/personalbest.ini`, this file will be updated after you record new lap times.

1. **Clone this repo**
```
git clone https://github.com/yeftakun/ac-lapboard
```
2. **Drop your data.** Copy `personalbest.ini` into `data/` and edit `src/data/config.json` based on your preferences.
> Found the file at `C:\User\<you>\Documents\Assetto Corsa\personalbest.ini`

> Gear options: `gamepad`, `wheel-pedal`, `keyboard-mouse`.
3. **Save change.**
```
git add .
git commit -m "update lap"
```
4. **Remove the remote**
```
git remote remove origin
```
5. **Push to your github** If you have github cli installed, run `gh repo create <your-repo-name> --public --source=. --remote=origin --push`. Otherwise, create a new repo on github.com and push manually.
6. **Match the workflow branch.** Ensure the branch listed in [`main.yml`](.github/workflows/main.yml) under `on: push: branches:` matches your repo’s default branch (e.g., `master` or `main`).
7. **Enable github pages** Go to your repo settings → Pages → Select **GitHub Actions** as source.
8. **Wait for the first deployment.** After pushing, go to the Actions tab and wait for the workflow to finish. Your site should be live at `https://<your-github-username>.github.io/<your-repo-name>/`.

> Note: Once you switch the Pages source to GitHub Actions, the site usually goes live but the dashboard may still show an error. You can ignore it—after the next workflow run (another push/commit or a manual run) the error status will clear.

## Get the latest updates
To pull in the latest updates from this template repo run `update-from-template.bat`. This script fetches and merges changes from the original repo.
> This updater script was added after the initial release. If you cloned the template before it existed, [download the script](https://github.com/yeftakun/ac-lapboard/releases/download/1.1.0/update-from-template.bat ) and place it in the repository root.

## Update your lap data
<details>
	<summary><b>Update manualy</b></summary>
	<ol>
		<li>Replace `data/personalbest.ini` with your latest lap data.</li>
		<li>Commit and push the changes.</li>
		<li>GitHub Actions will automatically rebuild and deploy your site.</li>
	</ol>	
</details>
<details>
	<summary><b>Lap Updater (New)</b></summary>
	<ol>
		<li>Requires: .NET 8</li>
		<li><a href="https://github.com/yeftakun/lap-updater/releases">Download app</a></li>
		<li>Run and follow the instruction on the app.</li>
	</ol>
</details>

## Preview on local
**Requirements:**
- Node.js v18+

1. `npm install` to install dependencies.
2. `npm run build` to convert INI and build the site.
3. `npm run dev` to start at `http://localhost:4321/`.

### Quick reference
- `npm run laps:convert` → convert INI without building.
- Update fonts/colors in `src/styles/globals.css` if you want a different vibe.
---

## Video
YouTube video already dropped!

[Assetto Corsa Web Laptime Archive | GitHub Pages Deploy](https://youtu.be/we6h3rqKdto?si=Dr0Gce8JuYq5cX8V)

[Lap Updater for Assetto Corsa Lap Archive | No Yap](https://youtu.be/x_tdR8pqQYU?si=Tb59H6niutRXcftF)

---

## FAQ

<details>
	<summary><b>Q: Is this free?</b></summary>
	A: Yep! The template is 100% free and open-source.
</details>

<details>
	<summary><b>Q: Do I need to know how to code?</b></summary>
	A: Nope. You just need to follow the steps in the tutorial. No coding skills required.
</details>

<details>
    <summary><b>Q: Do I need to pay for hosting or tools?</b></summary>
    A: Not at all. Everything used here is free, and GitHub Pages hosts your site for $0. Just make sure your repo is not private.
</details>

<details>
	<summary><b>Q: Why use this over other apps?</b></summary>
	A:
	<ul>
		<li><b>Full Control:</b> You own your data.</li>
		<li><b>Lightweight:</b> No background apps running while you race.</li>
		<li><b>Customizable:</b> Since you have the code, you can tweak the look however you like.</li>
	</ul>
</details>

<details>
	<summary><b>Q: Does it work with Mod tracks/cars?</b></summary>
	A: Yes! It reads directly from your <code>personalbest.ini</code>, so any track or car you drive will show up automatically.
</details>

<details>
	<summary><b>Q: How do I update my lap times?</b></summary>
	A: Just replace the <code>personalbest.ini</code> file in your repository and commit the changes. The site updates itself automatically.
</details>

<details>
	<summary><b>Q: Is the data validated / any anti-cheat?</b></summary>
	A: Nope. Since it reads from a simple text file, the numbers can be easily manipulated. But I trust you guys to keep it real... right? ...Right?
</details>

---
That’s it — swap the data, tweak config, and you’ve got a self-hosted Assetto Corsa lap archive.

