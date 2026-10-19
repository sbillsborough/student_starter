# StudentScores Python Program

A simple object-oriented Python program designed to collect student names and module scores, calculate their mean score, and display the formatted results.

---

## Table of Contents

- [Overview](#overview)
- [Class Design](#class-design)
- [Requirements & Features](#requirements--features)
- [Python Source Code (`student_scores.py`)](#python-source-code-student_scorespy)
- [How to Run](#how-to-run)
- [Example Output](#example-output)

---

## Overview

This project implements a Python class called `StudentScores` that stores details for a student and calculates their academic performance across four distinct modules:

- Mathematics
- Programming
- Research
- Networking

---

## Class Design

### Class: `StudentScores`

#### Constructor

```python
def __init__(self, name, mathematics, programming, research, networking)
```

Initializes the student's name and individual module scores as instance attributes.

#### Methods

- **`calculate_mean()`**: Computes the mean score across the four subjects using the formula:
  $$\text{Mean Score} = \frac{\text{Mathematics} + \text{Programming} + \text{Research} + \text{Networking}}{4}$$
- **`display_result()`**: Prints a summary of the student's details, individual module scores, and the calculated mean score.

---

## Requirements & Features

1. Prompts the user to enter a student's name.
2. Prompts the user for score inputs across four specified modules.
3. Features input validation to handle numeric conversions and prevent invalid entries.
4. Uses Object-Oriented Programming (OOP) concepts in Python.

---

## Python Source Code (`student_scores.py`)

Below is the code for `student_scores.py`:

```python
class StudentScores:
    """Class to store student module scores and calculate the average."""

    def __init__(self, name, mathematics, programming, research, networking):
        """Initialize the student's name and scores for four modules."""
        self.name = name
        self.mathematics = mathematics
        self.programming = programming
        self.research = research
        self.networking = networking

    def calculate_mean(self):
        """Calculate and return the mean score across all four modules."""
        total_scores = (
            self.mathematics + self.programming + self.research + self.networking
        )
        return total_scores / 4.0

    def display_result(self):
        """Display the student's details, individual scores, and calculated mean score."""
        mean_score = self.calculate_mean()
        print("\n" + "=" * 40)
        print("         STUDENT ACADEMIC REPORT         ")
        print("=" * 40)
        print(f"Student Name : {self.name}")
        print("-" * 40)
        print("Module Scores:")
        print(f"  - Mathematics : {self.mathematics:.2f}")
        print(f"  - Programming : {self.programming:.2f}")
        print(f"  - Research    : {self.research:.2f}")
        print(f"  - Networking  : {self.networking:.2f}")
        print("-" * 40)
        print(f"Mean Score    : {mean_score:.2f}")
        print("=" * 40 + "\n")


def get_valid_score(subject_name):
    """Helper function to prompt and validate float input for a score."""
    while True:
        try:
            score = float(input(f"Enter score for {subject_name}: "))
            if 0 <= score <= 100:
                return score
            else:
                print("Invalid entry. Score should be between 0 and 100.")
        except ValueError:
            print("Invalid input. Please enter a valid numerical value.")


def main():
    print("--- Student Scores Entry System ---\n")

    # 1. Ask the user to enter a student's name
    student_name = input("Enter student's name: ").strip()

    # 2. Ask the user to enter scores for four modules
    math_score = get_valid_score("Mathematics")
    prog_score = get_valid_score("Programming")
    res_score = get_valid_score("Research")
    net_score = get_valid_score("Networking")

    # 3 & 6. Create an object of the StudentScores class
    student = StudentScores(
        name=student_name,
        mathematics=math_score,
        programming=prog_score,
        research=res_score,
        networking=net_score,
    )

    # 7. Call the required method to display the final result
    student.display_result()


if __name__ == "__main__":
    main()
```

---

## How to Run

1. Ensure you have Python 3.x installed.
2. Clone this repository:
   ```bash
   git clone https://github.com/your-username/student-scores.git
   cd student-scores
   ```
3. Run the script:
   ```bash
   python student_scores.py
   ```

---

## Example Output

```text
--- Student Scores Entry System ---

Enter student's name: Alex Mercer
Enter score for Mathematics: 85.5
Enter score for Programming: 92.0
Enter score for Research: 78.0
Enter score for Networking: 88.5

========================================
         STUDENT ACADEMIC REPORT
========================================
Student Name : Alex Mercer
----------------------------------------
Module Scores:
  - Mathematics : 85.50
  - Programming : 92.00
  - Research    : 78.00
  - Networking  : 88.50
----------------------------------------
Mean Score    : 86.00
========================================
```
