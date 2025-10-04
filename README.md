# 🌐 Website Deployment mit GitHub Pages + eigener Domain

Dieses Dokument beschreibt Schritt für Schritt, wie du **kostenlos** eine professionelle Website mit eigener Domain, E-Mail-Adresse und GitHub Pages erstellst.  
Ideal für IT-Projekte, Portfolio-Seiten oder kleine Business-Webseiten.

---

## 🚀 Ziel

**Ziel:**  
Eine einfache, wartungsfreie und kostenlose Hosting-Lösung auf Basis von:
- GitHub Pages (Hosting)
- GoDaddy (Domainverwaltung)
- ImprovMX (E-Mail-Weiterleitung)
- Visual Studio Code (Entwicklung)

---

## 🧩 1. GitHub Repository erstellen

1. Gehe zu [https://github.com/new](https://github.com/new)
2. Repository-Name: z. B. `migrationservice`
3. Sichtbarkeit:
   - **Public** → öffentlich erreichbar  
   - **Private** → nur sichtbar für dich (nur mit GitHub Pro)
4. Klicke auf **Create Repository**

---

## 💻 2. Lokale Einrichtung in Visual Studio Code

```bash
git clone https://github.com/<username>/<repository>.git
cd <repository>
```

Dann den Ordner in **VS Code** öffnen.

---

## ⚙️ 3. Git konfigurieren (nur einmal nötig)

```bash
git config --global user.name "nordicduck"
git config --global user.email "nordicbear@gmail.com"
```

---

## 🧱 4. index.html erstellen

Beispiel:

```html
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Migrationservice</title>
</head>
<body>
  <header>
    <h1>Migrationservice</h1>
    <p>Professionelle IT-Migration & Beratung</p>
  </header>

  <main>
    <p>Ich unterstütze Unternehmen bei der Migration von IT-Systemen.</p>
    <img src="1.png" alt="Team bei der Arbeit" />
  </main>

  <footer>
    <p>&copy; <span id="year"></span> Migrationservice</p>
  </footer>

  <script>
    document.getElementById("year").textContent = new Date().getFullYear();
  </script>
</body>
</html>
```

---

## 🌍 5. GitHub Pages aktivieren

1. Öffne dein Repository auf GitHub  
2. Gehe zu **Settings → Pages**  
3. Unter *Source*:  
   - Branch: `main`  
   - Folder: `/ (root)`  
4. Nach ca. 1–2 Minuten erreichbar unter:  
   ```
   https://<username>.github.io/<repositoryname>/
   ```

---

## 🔗 6. Eigene Domain mit GoDaddy verbinden

### 1️⃣ CNAME-Datei anlegen
Erstelle eine Datei `CNAME` im Root-Ordner:

```
migrationservice.de
```

Commit und Push:
```bash
git add .
git commit -m "Add CNAME"
git push
```

### 2️⃣ DNS-Einträge bei GoDaddy
In der DNS-Verwaltung folgende Einträge setzen:

| Typ | Name | Wert | TTL |
|------|------|------|-----|
| **A** | @ | 185.199.108.153 | 1 Stunde |
| **A** | @ | 185.199.109.153 | 1 Stunde |
| **A** | @ | 185.199.110.153 | 1 Stunde |
| **A** | @ | 185.199.111.153 | 1 Stunde |
| **CNAME** | www | `<username>.github.io` | 1 Stunde |

Nach etwa 30–60 Minuten ist die Domain aktiv:
👉 https://migrationservice.de

---

## 🧑‍💼 7. E-Mail mit eigener Domain (über ImprovMX)

Kostenloser Weiterleitungsdienst → [https://improvmx.com](https://improvmx.com)

1. Domain hinzufügen: `migrationservice.de`
2. MX-Einträge in GoDaddy eintragen:

| Typ | Name | Wert | Priorität | TTL |
|------|------|------|------------|------|
| MX | @ | mx1.improvmx.com | 10 | 1 Stunde |
| MX | @ | mx2.improvmx.com | 20 | 1 Stunde |

3. In ImprovMX Weiterleitung einrichten:
   ```
   info@migrationservice.de → nordicbaer@gmail.com
   ```

4. Teste die Adresse durch eine Testmail.

---

## 📤 8. Änderungen hochladen

```bash
git add .
git commit -m "Update Website"
git push
```

Die Seite aktualisiert sich automatisch innerhalb weniger Minuten.

---

## 🧪 9. Lokal testen mit Live Server

1. In VS Code „Live Server“ Erweiterung installieren  
2. Rechtsklick auf `index.html` → **Open with Live Server**  
3. Browser öffnet sich unter:
   ```
   http://localhost:5500
   ```

---

## 🧰 10. Setup für weitere Webseiten wiederverwenden

Wenn du weitere Projekte anlegst:

| Projekt | Domain | GitHub Repo | Beispiel |
|----------|---------|--------------|-----------|
| Migrationservice | migrationservice.de | migrationservice | GitHub Pages |
| IT-Service | it-basti.com | it-basti | GitHub Pages |
| Portfolio | basti.info | basti-info | GitHub Pages |

💡 Einfach:
- Neues Repo anlegen  
- CNAME anpassen  
- DNS-Records in GoDaddy ändern  
- Optional E-Mail mit ImprovMX einrichten

---

## ✅ Zusammenfassung

| Bereich | Dienst | Kosten | Zweck |
|----------|--------|--------|-------|
| **Hosting** | GitHub Pages | Kostenlos | Website |
| **Domain** | GoDaddy | ca. 10–15 €/Jahr | Domainverwaltung |
| **E-Mail** | ImprovMX | Kostenlos | E-Mail-Weiterleitung |
| **Editor** | VS Code | Kostenlos | Entwicklung & Deployment |

---

© 2025 Basti — Migrationservice & IT-Consulting
