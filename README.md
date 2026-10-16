
jobs = {
    "Python Developer": ["python", "programming", "git", "oops"],
    "Data Analyst": ["python", "sql", "excel", "statistics", "power bi"],
    "Web Developer": ["html", "css", "javascript", "web design"],
    "Software Tester": ["testing", "python", "sql", "debugging"],
    "Data Scientist": ["python", "machine learning", "statistics", "pandas"],
    "Cybersecurity Analyst": ["networking", "linux", "security", "python"],
    "UI/UX Designer": ["design", "creativity", "figma", "ui", "ux"],
    "Digital Marketer": ["marketing", "seo", "content writing", "analytics"],
    "HR Executive": ["communication", "recruitment", "management"],
    "IT Support": ["troubleshooting", "networking", "communication"]
}

print("=== Skill2Career Job Recommendation ===")
print("Enter your skills separated by commas.")
user_skills = input("Your skills: ").lower().split(",")
user_skills = {s.strip() for s in user_skills if s.strip()}

results = []

for job, required in jobs.items():
    matched = user_skills.intersection(required)
    score = len(matched) / len(required) * 100
    if matched:
        missing = set(required) - user_skills
        results.append((score, job, matched, missing))

results.sort(reverse=True)

if not results:
    print("No matching job found. Try adding more skills.")
else:
    print("\nBest matching jobs for you:")
    for score, job, matched, missing in results[:3]:
        print(f"\nJob: {job}")
        print(f"Skill match: {score:.0f}%")
        print("Matched skills:", ", ".join(sorted(matched)))
        print("Skills to learn:", ", ".join(sorted(missing)) or "None")

    print("\nNote: Recommendations depend on the skills database.")

