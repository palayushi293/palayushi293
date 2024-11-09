<h3>- 👋 Hi, I’m  Ayushi Pal
  </h3>
  
  <h3>
- 👀 I’m interested in frontend and Machine Learning
  </h3>

  <h3>
- 🌱 I’m currently learning React, CNN
  </h3>

  <h3>
- 💞️ I’m looking for real world project.
  </h3>


import requests
import json

def fetch_leetcode_data(username):
    url = https://leetcode.com/u/AYUSHI_PAL/"
    query = """
    query getUserProfile($username: String!) {
        matchedUser(username: $username) {
            username
            profile {
                reputation
                ranking
            }
            submitStats {
                acSubmissionNum {
                    difficulty
                    count
                    submissions
                }
            }
        }
    }
    """
    variables = {"username": username}
    response = requests.post(url, json={"query": query, "variables": variables})
    return response.json()

def update_readme(data):
    with open("README.md", "r") as file:
        content = file.readlines()

    # Insert or replace LeetCode stats in README.md
    start = content.index("<!-- LeetCode-Stats-Start -->\n")
    end = content.index("<!-- LeetCode-Stats-End -->\n")
    content[start + 1:end] = [f"User: {data['username']}\n",
                              f"Reputation: {data['profile']['reputation']}\n",
                              f"Ranking: {data['profile']['ranking']}\n",
                              f"Solved Problems: {data['submitStats']['acSubmissionNum'][0]['count']}\n"]

    with open("README.md", "w") as file:
        file.writelines(content)

# Replace 'your-username' with your actual LeetCode username
data = fetch_leetcode_data("https://leetcode.com/u/AYUSHI_PAL/")
update_readme(data)






<!---
palayushi293/palayushi293 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
